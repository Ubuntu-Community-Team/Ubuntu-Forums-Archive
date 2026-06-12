---
title: "Where is my GUI...help!"
date: 2007-04-05
forum: General Help
---

### Post by djseto on 2007-04-05
I installed 6.10d (64bit) today in hopes of getting my MythTV box running. When the PC turns out, I get to the login screen and I enter my username and password and all I get is a blank background. No icon, menus, ect. When I right click, it says OpenBox 3 with the ability to click on terminal emulator, web browser, desktops obConf, Reconfigure,Restart, and Exit. Nothing comes up if i try webbrowser, but terminal emulator works.

Prior to logging in, if i change my session to GNOME from Open Box, etc, I still get the same thing. Its been driving me nuts for hours and google hasnt helped. please help!

---

### Post by crispy_420 on 2007-04-05
Have you looked at [LinuxMCE]("http://linuxmce.com/")? Looks to be a very promising PVR solution.

---

### Post by djseto on 2007-04-06
no. but I havent even gotten to the mythTV install.. I just want to know what is wrong with my GUI??

---

### Post by aysiu on 2007-04-06
OpenBox, like a lot of window managers, requires a lot of tweaking before it can be usable in a point-and-click fashion.

I would recommend IceWM.

---

### Post by djseto on 2007-04-06
I dont want to use open box. I'm using this install guide: [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

If you can point me to another GUI for Ubunutu, that would be great. I just need the full command line: sudo apt-get install XXXXX

---

### Post by aysiu on 2007-04-06
Well, instead of doing ```
sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu
``` you can do ```
sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm icewm iceconf iceme icepref icewm-gnome-support icewm-themes gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu
```

---

