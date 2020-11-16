cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

add_definitions(-std=c++11)
add_definitions(-w)

set(CXX_FLAGS "-Wall")
set(CMAKE_CXX_FLAGS, "${CXX_FLAGS}")

project(playback)

#find_package(PCL 1.8 REQUIRED)
find_package(PCL 1.8 REQUIRED PATHS ${PROJECT_SOURCE_DIR}/3rd_party/pcl)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
list(REMOVE_ITEM PCL_LIBRARIES "vtkproj4")


add_executable (environment src/environment.cpp src/render/render.cpp src/processPointClouds.cpp)
target_link_libraries (environment ${PCL_LIBRARIES})




