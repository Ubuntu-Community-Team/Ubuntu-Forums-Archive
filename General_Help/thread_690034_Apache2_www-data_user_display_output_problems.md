---
title: "Apache2 www-data user display output problems"
date: 2008-02-07
forum: General Help
---

### Post by OsirisBlue on 2008-02-07
Hi, I am having a bit of a problem executing a PHP exec function in Ubuntu 7.10 using Apache2. 

When the exec function is called, it is meant to open an application window (such as a media player), but is giving an unable to display error in the apache error log file, even if the called application is only meant to write output to the terminal. I have executed the php file directly from terminal and it works fine, which indicates that the user that is apache (www-data) does not have permission to write to the display. I have worked with permissions for the user, modified the sudoers file, tried adding www-data to the xserver local list (xhost +local:www-data@) and even modifying the passwd file giving www-data root access, all without success. The only other thing I can think of is going through the php.ini file and seeing if maybe something in there is causing it but this is unlikely because the page executed fine through the terminal. Any help in this regard would be greatly appreciated. Below is a copy of the error messages I am receiving:

** CRITICAL **: Unable to open display

VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 33 (www-data)
[00000288] skins2 interface error: Cannot open display
[00000288] skins2 interface error: cannot initialize OSFactory
Error: Unable to initialize gtk, is DISPLAY set properly?

---

