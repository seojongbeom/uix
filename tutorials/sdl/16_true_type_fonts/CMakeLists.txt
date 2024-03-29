cmake_minimum_required(VERSION 3.22)
project(SDL_16_true_type_fonts)

set(CMAKE_CXX_STANDARD 17)

FIND_PACKAGE(blend2d)
FIND_PACKAGE(SDL2)
FIND_PACKAGE(SDL2_image)
FIND_PACKAGE(Freetype)
FIND_PACKAGE(PNG)
FIND_PACKAGE(harfbuzz)
FIND_PACKAGE(ZLIB)

include_directories(${SDL2_ttf_SOURCE_DIR})
add_definitions(-DSDK_ROOT_PATH="${CMAKE_PREFIX_PATH}")
add_executable(${PROJECT_NAME} main.cpp)

SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static")

target_link_libraries(${PROJECT_NAME} ${blend2d_LIBRARIES} ${SDL2_LIBRARIES}-static SDL2_image::SDL2_image-static SDL2_ttf Freetype::Freetype harfbuzz::harfbuzz ${PNG_LIBRARIES} ${ZLIB_LIBRARIES})