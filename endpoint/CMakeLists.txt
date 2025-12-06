cmake_minimum_required(VERSION 3.30)
project(endpoint)
set(CMAKE_CXX_STANDARD 20)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) 

find_package(Boost REQUIRED)

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)
add_library(common SHARED ${SRC_LIST})

target_include_directories(common PUBLIC ${PROJECT_SOURCE_DIR}/include)

add_executable(main main.cpp)

target_include_directories(main PUBLIC ${PROJECT_SOURCE_DIR}/include)

target_link_libraries(main PUBLIC Boost::headers)
