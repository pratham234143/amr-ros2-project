Steps :-

COMMANDS FOR FIRST RUN(CREATING MAP)

command1:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch gazebo_ros gazebo.launch.py world:=/home/professor/office.world

#opens gazebo with office.world which is our custom world

command2:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo robot_state_publisher.launch.py use_sim_time:=true

#This tells ROS 2 where the Lidar and wheels are physically located
#publish robot state

command3:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=true

#slam creates map for the world

command4:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 run turtlebot3_teleop teleop_keyboard

#enables user to drive the robot

command5:-
source /opt/ros/humble/setup.bash
ros2 run nav2_map_server map_saver_cli -f /home/professor/office_map

#saves the map created in slam


COMMANDS FOR SECOND RUN (NAVIGATION)

command1:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch gazebo_ros gazebo.launch.py world:=/home/professor/office.world

#opens gazebo with office.world which is our custom world

command2:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo robot_state_publisher.launch.py use_sim_time:=true

#This tells ROS 2 where the Lidar and wheels are physically located
#publish robot state

command3:-
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=true map:=/home/professor/office_map.yaml

#opens navigation to send goals 
