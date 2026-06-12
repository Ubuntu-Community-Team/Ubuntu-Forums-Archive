---
title: "Switch user not working"
date: 2020-05-11
forum: General Help
---

### Post by Alligator on 2020-05-11
I've recently changed a failed video card and added a second monitor. At the login screen, everything is fine, but if I try to switch users the screens go blank. After a long period of time, the login screen appears. (long being over night)  Also, ctrl alt F? does not work.  I'm using 18.04, trying to get it all working and backed up before switch to 20.04  I've searched the net and this forum and have been unsuccessful in finding a similar thread. Not sure about the advance search either, can't even find my own threads.  In any event, my boss (the wife) likes to play games, so I'm in trouble. I Can't let her out of the house, so I'm in trouble.  Your help would be greatly appreciated.  Thank you

Ron

---

### Post by CelticWarrior on 2020-05-11
Please post the graphics card you're using now, the drivers version if user installed, other hardware specifications and type of connection with the monitors.

---

### Post by Alligator on 2020-05-11
```

Using NVIDIA driver metapackage from nvidia-440(open-source)

Processor AMD Ryzen5 2400g with radeon vega graphics x8
Gnome 3.28.2
OS type 64 bit

ron@localhost:~$ xrandr --query
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
DVI-D-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00 +  60.00*   59.94    50.00    29.97    25.00    23.98  
   1280x1024     60.02  
   1280x720      60.61    59.94    50.00  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       59.95    59.94    59.93  
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00 +  74.99*   59.94    50.00  
   1680x1050     59.95  
   1440x900      59.89  
   1440x576      50.00  
   1440x480      59.94  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)


Monitors
Main - ASUS VP278
2nd   DX24L200A12


```

---

### Post by Alligator on 2020-05-11
I installed the driver
sudo apt-get purge 'nvidia*'
sudo add-apt-repository ppa:graphics-drivers

sudo apt-get install ubuntu-drivers-common
sudo ubuntu-drivers autoinstall

also did a update and restart.

This worked and eliminated an xconfig error. 
using HDMI for main monitor and DVI for second.

---

