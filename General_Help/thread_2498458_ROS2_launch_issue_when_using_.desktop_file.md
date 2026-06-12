---
title: "ROS2 launch issue when using .desktop file"
date: 2024-06-14
forum: General Help
---

### Post by fujiguy462 on 2024-06-14
[h=1]I am having an odd problem and hoping someone can assist. I am using Ubuntu desktop 22.04 and ROS2 humble. I have a TOF camera that I am setting up for a project. Currently I have the camera drivers installed and working and I can view the topics in RVIZ2 locally and on a remote machine.[/h]The issue is, I have written a simple bash script to source the environment and call the ros2 launch file and this works great if I open a terminal and call the script. I have also created a .desktop file to call the script and it open as terminal and appears to work but I cannot access the topics in RVIZ2. I cannot see where the issue would be why it would work one way but not the other, any help is appreciated. I have included a copy of the script and .desktop file below. FYI I have tried the desktop file with terminal true and not using gnome-terminal as well as not calling the script and adding it all to the exec and they all act the same way.

ros_launch.sh:
```
#! /bin/bash

source /opt/ros/humble/setup.bash
source /home/lidar/lidar_ws/src/install/setup.bash

echo -e "\033[6;32mLaunching ROS camera drivers, Please wait....\n\n\\033[0m"
ros2 launch synexens_ros2 driver_launch.py
```
.desktop file:
```
[Desktop Entry]
Type=Application
Terminal=false
Name=ROS PointCloud
Icon=/home/lidar/lidar_ws/radar.png
Exec=gnome-terminal -e "bash -c '/home/lidar/ros_launch.sh;$SHELL'"
```

---

