cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_MODULE_PATH_BACKUP ${CMAKE_MODULE_PATH})
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

if(LINUX)
    find_package(ICU COMPONENTS uc io REQUIRED)
    include_directories(${CMAKE_SOURCE_DIR})
    include_directories(${ICU_INCLUDE_DIRS})
endif()


set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH_BACKUP})

project(MikuMikuFormats)

add_library(pmx Pmx.cpp)
target_link_libraries(pmx PRIVATE ${ICU_LIBRARIES})
