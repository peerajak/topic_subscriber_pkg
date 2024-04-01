cmake_minimum_required(VERSION 2.8.3)
project(topic_subscriber_pkg)


find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  message_generation
)

add_message_files(
  FILES
  Age.msg
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(
  CATKIN_DEPENDS roscpp std_msgs message_runtime
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(simple_topic_subscriber src/simple_topic_subscriber.cpp)
add_dependencies(simple_topic_subscriber ${simple_topic_subscriber_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(simple_topic_subscriber
   ${catkin_LIBRARIES}
 )


