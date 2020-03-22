cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(example-app)

# 查找当前目录下的所有源文件  
# 并将名称保存到 DIR_ROOT_SRCS变量  
aux_source_directory(. DIR_ROOT_SRCS)  
  
#添加opencv头文件的搜索路径    
INCLUDE_DIRECTORIES(D:/Opencv3.4.0/opencv/build/include)  
INCLUDE_DIRECTORIES(D:/Opencv3.4.0/opencv/build/include/opencv2)  
INCLUDE_DIRECTORIES(D:/Opencv3.4.0/opencv/build/include/opencv)  
  
# 添加链接库    
#添加动态库的路径
# link_libraries用在add_executable之前，target_link_libraries用在add_executable之后
# link_libraries用来链接静态库，target_link_libraries用来链接导入库，即按照header file + .lib + .dll方式隐式调用动态库的.lib库
link_directories("D:/Opencv3.4.0/opencv/build/x64/vc15/lib/")
link_libraries(opencv_world340.lib)

add_executable(example-app main.cpp)
# link_directories(/usr/local/lib)   'find_package' has already done this

#target_link_libraries(example-app "${OpenCV_LIBS}")
set_property(TARGET example-app PROPERTY CXX_STANDARD 11)