---
title: "HELP please EXP Graphics Card V6.0 External adapter on UBUNTU"
date: 2016-10-20
forum: General Help
---

### Post by larry41 on 2016-10-20
hi friends i bought an express graphic card adapter 6.0 for my elitebook 8470p i'm running ubuntu 16.04 Intel® Core&#8482; i5-3360M CPU @ 2.80GHz × 4 Intel® Ivybridge Mobile 64-bit Memory 7.7 GiB . please could anyone tell me how can i install the driver properly for the external graphic card EVGA GEFORCE GTX 760 without provoking conflict with the internal one? i have NO any problem on disable it that  internal graphic card but i don't even know how to do it. please help me i want to use for my blender rendering. i will give you all the outputs of any command you tell me.

---

### Post by larry41 on 2016-10-20
friends to see what type of graphic card i have internal i put this command on terminal lspci -k | grep -A 2 -i "VGA"
 and this is what i got
```

larry3d@larry3d:~$ lspci -k | grep -A 2 -i "VGA"
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    DeviceName: 64
    Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller
larry3d@larry3d:~$ ^C
larry3d@larry3d:~$ 



```
after that i type the next command on terminal software-properties-gtk 


```


larry3d@larry3d:~$ software-properties-gtk
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
larry3d@larry3d:~$ 

```
softwares updates it pop up but it didn't show any software from Nvidia to install as you can see in the picture [ATTACH=CONFIG]271699[/ATTACH] please can anyone help me

---

### Post by larry41 on 2016-10-20
guys i found out first i have to do this command 
sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime

but then i'm getting some problems here is what i got
```

larry3d@larry3d:~$ sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-319 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nvidia-319' has no installation candidate
E: Unable to locate package nvidia-settings-319
larry3d@larry3d:~$ 



```
could anyone tell me please what do i need to do

---

### Post by colmax on 2016-10-20
Maybe settings>software&updates>additional drivers
Should be able to choose your video driver from there
Cheers

---

### Post by colmax on 2016-10-20
Or go to nvidia site for linux drivers

---

### Post by larry41 on 2016-10-20
aditional softwares is not showing any other software and my adapter with the graphic card is running right now

[ATTACH=CONFIG]271702[/ATTACH] 
on this link  i found that tutorial that's why is weird nothing is showing on aditionals  [https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu](https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu)

---

