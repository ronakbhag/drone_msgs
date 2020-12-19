cmake_minimum_required(VERSION 2.8.3)
project(drone_msgs)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

# search for everything we need to build the messages, dont forget the message_generation
find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  nav_msgs
  tf
  mavros_msgs
  roscpp
  drone_common
  message_generation
)

# Generate messages in the 'msg' folder
add_message_files(
  FILES
  waypoint.msg
)

# Generate services in the 'srv' folder
add_service_files(
  FILES
  commandPath.srv
  commandSetpoint.srv
)


## Generate actions in the 'action' folder
# add_action_files(
#   FILES
#   Action1.action
#   Action2.action
# )

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
  #   mavros_msgs
  #   moveit_msgs
)

# # search for all msg files
# FILE(GLOB messages_to_build RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/msg"
#     "${CMAKE_CURRENT_SOURCE_DIR}/msg/*.msg")

# # notify catkin to look at the previously found msg files
# add_message_files(
#   FILES
#   ${messages_to_build}
# )

# export the dependencis of this package for who ever depends on us
catkin_package()

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${drone_common_INCLUDE_DIRS}
)
