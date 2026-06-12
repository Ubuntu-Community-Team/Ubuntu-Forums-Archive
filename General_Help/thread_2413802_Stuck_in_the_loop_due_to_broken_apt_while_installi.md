---
title: "Stuck in the loop due to broken apt while installing ROS Melodic on Ubuntu 18.04 LTS"
date: 2019-03-02
forum: General Help
---

### Post by ravi_joshi on 2019-03-02
This issue may be related to ROS completely, however, at present, I am not sure about the source of the error. Hence I am posting it in this big community. I am trying to install [ROS Melodic]("http://wiki.ros.org/melodic/Installation/Ubuntu") on Ubuntu 18.04.2 LTS PC. Unfortunately, the command sudo apt install ros-melodic-desktop-full failed. Below is the output of the same command, when running again:


```

ravi@lab:~$ sudo apt install ros-melodic-desktop-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ros-melodic-desktop-full is already the newest version (1.4.1-0bionic.20190204.220757).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python-rosdistro-modules : Depends: python-rospkg-modules but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```


It suggests running apt --fix-broken install which I did but it doesn't solve the issue. See below:


```

ravi@lab:~$ sudo apt  --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libllvm6.0:i386 python-genmsg python-genpy python-roscpp-msgs python-rosgraph python-rosgraph-msgs python-std-msgs x11proto-dri2-dev x11proto-gl-dev
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python-rospkg-modules
The following NEW packages will be installed:
  python-rospkg-modules
0 upgraded, 1 newly installed, 0 to remove and 53 not upgraded.
461 not fully installed or removed.
Need to get 0 B/23.4 kB of archives.
After this operation, 133 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 542662 files and directories currently installed.)
Preparing to unpack .../python-rospkg-modules_1.1.7-1_all.deb ...
Unpacking python-rospkg-modules (1.1.7-1) ...
dpkg: error processing archive /var/cache/apt/archives/python-rospkg-modules_1.1.7-1_all.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/rospkg/manifest.py', which is also in package python-rospkg 1.1.4-1
Errors were encountered while processing:
 /var/cache/apt/archives/python-rospkg-modules_1.1.7-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```






I thought of running update and upgrade but got stuck in the same issue. Please see below:


```

ravi@lab:~$ sudo apt update
Hit:1 http://ny-mirrors.evowise.com/ubuntu bionic InRelease
Hit:2 http://linux.teamviewer.com/deb stable InRelease                                                                                                           
Hit:3 http://ny-mirrors.evowise.com/ubuntu bionic-updates InRelease                                                                                              
Hit:4 http://ny-mirrors.evowise.com/ubuntu bionic-backports InRelease                                                                      
Hit:5 http://ny-mirrors.evowise.com/ubuntu bionic-security InRelease                                                 
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                                                         
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                                                                     
Hit:8 http://packages.ros.org/ros/ubuntu bionic InRelease                                                                      
Hit:10 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu bionic InRelease                              
Hit:12 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu bionic InRelease                              
Hit:11 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease                       
Hit:13 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic InRelease
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
53 packages can be upgraded. Run 'apt list --upgradable' to see them.
ravi@lab:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python-rosdistro-modules : Depends: python-rospkg-modules but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```




I also tried removing the ros-melodic-desktop-full package but got in vain as shown below:


```

ravi@lab:~$ sudo apt purge --remove ros-melodic-desktop-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python-rosdistro-modules : Depends: python-rospkg-modules but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```


I am not able to proceed. Below is the more information about the PC:


```

ravi@lab:~$ uname -a
Linux lab 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
ravi@lab:~$ cat /etc/issue
Ubuntu 18.04.2 LTS \n \l





``` 


Any workaround, please?

---

### Post by ravi_joshi on 2019-03-04
Any suggestions, please?

---

