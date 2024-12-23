cmake_minimum_required(VERSION 3.10)
project(yolov8ncnn)

set(CMAKE_CXX_STANDARD 11)

set(OpenCV_DIR /Users/oliwiarewer/AndroidStudioProjects/ncnn-android-yolov8-pose/app/src/main/jni/opencv-mobile-3.4.20-android/sdk/native/jni)
set(ncnn_DIR /Users/oliwiarewer/AndroidStudioProjects/ncnn-android-yolov8-pose/app/src/main/jni/ncnn-20240820-android-vulkan/arm64-v8a/lib/cmake/ncnn)

set(ANDROID_NDK /Users/oliwiarewer/Library/Android/sdk/ndk/27.0.12077973)

include(${ANDROID_NDK}/build/cmake/android.toolchain.cmake)

find_package(OpenCV REQUIRED)
find_package(ncnn REQUIRED)



add_library(yolov8ncnn SHARED yolov8ncnn.cpp yolov8.cpp ndkcamera.cpp yolov8pose.cpp)

target_link_libraries(yolov8ncnn ncnn ${OpenCV_LIBS} camera2ndk mediandk)
