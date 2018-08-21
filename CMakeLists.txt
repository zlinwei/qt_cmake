cmake_minimum_required(VERSION 3.10)

project(qt_test LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_PREFIX_PATH /Users/linwei/qt/5.11.1/clang_64/lib/cmake)
# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
# Instruct CMake to run moc automatically when needed
set(CMAKE_AUTOMOC ON)
# Create code from a list of Qt designer ui files
set(CMAKE_AUTOUIC ON)

# Find the QtWidgets library
find_package(Qt5Widgets CONFIG REQUIRED)
find_package(Qt5Core CONFIG REQUIRED)

include_directories(${Qt5Widgets_INCLUDE_DIRS})
add_definitions(${Qt5Widgets_DEFINITIONS})
set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} ${Qt5Widgets_EXECUTABLE_COMPILE_FLAGS})

set(qt_test_SRCS
        form.ui
        form.cpp
        main.cpp
        )

add_executable(qt_test ${qt_test_SRCS})
target_link_libraries(qt_test PUBLIC
        Qt5::Core Qt5::Gui Qt5::Widgets)