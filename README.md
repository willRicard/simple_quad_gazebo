# simple_quad_gazebo
Very simple quadcopter for Gazebo using ROS1 Noetic. It's just a very cheap and dirty adaptation of a pre-existent Gazebo plugin called "hand of god", but now it looks like a quadcopter and you can send velocity commands too. In addition to that, it makes the quad **look** a little bit more realistic by **faking** the pitch and roll angles according to the acceleration. All settings are easy to understand, just check the [simple_quad.urdf](src/simple_quad/src/description/simple_quad.urdf).
Ricardo wrote this because he wanted something faster than the quad plugins available for Gazebo, but he wrote the code without worrying about writing an optimized code and we never tested it against anything to confirm it's really faster than those plugins.

```
catkin_make
```

```
. devel/setup.bash
```

```
roslaunch simple_quad display.launch
```

Move to Z=0.5:
```
rostopic pub /cmd_pos geometry_msgs/Pose "position:
  x: 0.0
  y: 0.0
  z: 0.5
orientation:
  x: 0.0
  y: 0.0
  z: 0.0
  w: 1.0" -1
```

Spin around Z with velocity 0.5rad/s:
```
rostopic pub /cmd_vel geometry_msgs/Twist "linear:
  x: 0.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.5" -1
```

Control it using the keyboard:
```
rosrun teleop_twist_keyboard teleop_twist_keyboard
```
