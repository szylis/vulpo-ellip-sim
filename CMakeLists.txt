cmake_minimum_required(VERSION 3.10)
project(EllipSim)

set(CMAKE_CXX_STANDARD 17)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

# ImGui sources
set(IMGUI_DIR thirdparty/imgui)
set(IMGUI_SRC
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)

# ImPlot sources
set(IMPLOT_DIR thirdparty/implot)
set(IMPLOT_SRC
    ${IMPLOT_DIR}/implot.cpp
    ${IMPLOT_DIR}/implot_items.cpp
)

add_executable(EllipSim
    src/main.cpp
    ${IMGUI_SRC}
    ${IMPLOT_SRC}
)

target_include_directories(EllipSim PRIVATE
    ${IMGUI_DIR}
    ${IMGUI_DIR}/backends
    ${IMPLOT_DIR}
)

target_link_libraries(EllipSim PRIVATE
    glfw
    OpenGL::GL
)
