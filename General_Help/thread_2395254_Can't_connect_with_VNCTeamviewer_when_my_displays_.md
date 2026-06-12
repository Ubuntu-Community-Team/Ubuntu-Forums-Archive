---
title: "Can't connect with VNC/Teamviewer when my displays are switched off"
date: 2018-06-29
forum: General Help
---

### Post by nachazo on 2018-06-29
Hello.
Since updating to 18.04 I have a problem connecting with VNC or Teamviewer.

It happens **only when I switch off my displays/monitors** (I have two displays). If I try to connect via VNC o Teamviewer with the monitors on (active or with enery saving mode, locked or not, don't mind) everything works ok, but if I do the same with the displays off, the X/gnome/whatever (I dont know) appears to be freezed, no dock, no menus, just some icons and texts and then the image freezes.

If I do the same with the system locked, the login screen appears but with elements misplaced (like a enormous resolution), I can make the login, but then the previous described problem appears. Freezes.

If I switch on the display... the things fixes! All works after some seconds (or alt+f2 "r")...

I tried this solution, but no works: [https://ubuntuforums.org/showthread.php?t=1297815](https://ubuntuforums.org/showthread.php?t=1297815)
Another similar solutions removes the device/output at reboot so I had to connect with ssh and remove the conf file...

I don't know how to do: this is so common; you use your pc with your displays, then lock the screen and switch off that and you want to connect remote... why I can't? With 16.04 worked for me!

Thanks!

Some info inxi -G:

> Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz, 1280x1024@60.02hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop version: 4.5 Mesa 18.0.0-rc5

---

