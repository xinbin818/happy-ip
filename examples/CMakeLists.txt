﻿if (NOT DEFINED BOOST_LIB_DIR)
	message( FATAL_ERROR "not define BOOST_LIB_DIR" )
endif()

include_directories(./ ${PROJECT_SOURCE_DIR}/src ${PROTOBUF_INCLUDE_DIR})
LINK_DIRECTORIES(${BUILD_DIR} ../${BOOST_LIB_DIR} ../${PROTOBUF_LIB_DIR} ../${GLOG_LIB_DIR})
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

##############################编译tcp_server#####################################
#程序名
set(OUT_NAME tcp_server)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./tcp_server.cpp" "./utils.h" "./server_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip)
#SET(CMAKE_EXE_LINKER_FLAGS " -no-pie")
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译tcp_client#####################################
#程序名
set(OUT_NAME tcp_client)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./tcp_client.cpp" "./utils.h" "./client_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip)
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译udp_server#####################################
#程序名
set(OUT_NAME udp_server)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./udp_server.cpp" "./utils.h" "./server_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip)
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译udp_client#####################################
#程序名
set(OUT_NAME udp_client)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./udp_client.cpp" "./utils.h" "./client_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip)
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)

#RETURN()

#if (NOT DEFINED PROTOBUF_INCLUDE_DIR OR NOT DEFINED PROTOBUF_LIB_DIR)
#	message( FATAL_ERROR "not define PROTOBUF" )
#endif()

##############################编译tcp_server_proto###############################
#程序名
set(OUT_NAME tcp_server_proto)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./tcp_server_proto.cpp" "./utils.h" "./dmo.pb.*" "./proto_server_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip network protobuf)
if (GLOG_OUTPUT)
	target_link_libraries(${OUT_NAME} glog)
endif()
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译tcp_client_proto###############################
#程序名
set(OUT_NAME tcp_client_proto)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./tcp_client_proto.cpp" "./utils.h" "./dmo.pb.*" "./proto_client_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip network protobuf)
if (GLOG_OUTPUT)
	target_link_libraries(${OUT_NAME} glog)
endif()
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译udp_server_proto###############################
#程序名
set(OUT_NAME udp_server_proto)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./udp_server_proto.cpp" "./utils.h" "./dmo.pb.*" "./proto_server_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip network protobuf)
if (GLOG_OUTPUT)
	target_link_libraries(${OUT_NAME} glog)
endif()
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
##############################编译udp_client_proto###############################
#程序名
set(OUT_NAME udp_client_proto)
#可执行程序
file(GLOB_RECURSE SOURCE_FILES "./udp_client_proto.cpp" "./utils.h" "./dmo.pb.*" "./proto_client_message_factory.*")
add_executable(${OUT_NAME} ${SOURCE_FILES})
#连接库
target_link_libraries(${OUT_NAME} ip network protobuf)
if (GLOG_OUTPUT)
	target_link_libraries(${OUT_NAME} glog)
endif()
target_link_libraries(${OUT_NAME} boost_system boost_thread Threads::Threads)
