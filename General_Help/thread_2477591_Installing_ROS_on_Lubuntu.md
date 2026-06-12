---
title: "Installing ROS on Lubuntu?"
date: 2022-07-31
forum: General Help
---

### Post by bengodfrey on 2022-07-31
Hello there,

I am running Lubuntu on an old laptop as I need an Ubuntu based OS to install 'ROS Noetic' to control a robotic arm. I followed the Trossen Robotics tutorial ([https://www.trossenrobotics.com/docs/interbotix_xsarms/ros_interface/index.html](https://www.trossenrobotics.com/docs/interbotix_xsarms/ros_interface/index.html)) on how to install 'ROS Noetic' on an Ubuntu system and I ran into errors (See attached).

Any suggestions on how to bypass these errors?

Thanks,
Ben

---

### Post by coffeecat on 2022-07-31
Since Lubuntu is an official Ubuntu flavour, I have moved your thread from the other Operating Systems section to General Help in the Ubuntu Official Flavours Support section.

The first two lines of your posted screenshot messages explain clearly why you are getting those errors. You are running the 22.04 release, which is not supported by the Interbotix software. The second line states that Interbotix only works with the 18.04 and 20.04 releases. Which leaves you little choice since Lubuntu 18.04 (which has a shorter supported life than Ubuntu) is now end of life.

---

### Post by HermanAB on 2022-08-01
Note that these kind of specialist tools are usually best installed on a dedicated ‘engineering’ machine, be that an old laptop or a Raspberry Pi.  Then, once the setup is working, turn automatic updates off and don’t change anything, since your tools may stop working following an update. 

If you have only one machine available, then install a virtualizer and create a dedicated virtual machine for your experiments, so that you don’t mess up your host.

---

