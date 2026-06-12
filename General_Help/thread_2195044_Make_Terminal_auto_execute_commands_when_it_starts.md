---
title: "Make Terminal auto execute commands when it starts up"
date: 2013-12-22
forum: General Help
---

### Post by nyanlinarsenal94 on 2013-12-22
Hi , I'm running Ubuntu 13.04 and I am wondering how I make the TERMINAL auto execute commands as soon as I start it up. I mean , I have been using ROS and I have to run the command ```
source /opt/ros/hydro/setup.bash
``` everytime I want to use ROS, which means that every new TERMINAL I start up , I also have to include this line so that I can start using ROS. Is there a way to include this line in the start up of TERMINAL so that it auto executes the code whenever I start a new TERMINAL instead of manually having to type that line everytime? I'll really appreciate the help. Thanks in advance.

---

### Post by deadflowr on 2013-12-22
Add it to your .bashrc file.
gedit ~/.bashrc
then add the command/executing-file and save.
Then it should load everytime.

---

