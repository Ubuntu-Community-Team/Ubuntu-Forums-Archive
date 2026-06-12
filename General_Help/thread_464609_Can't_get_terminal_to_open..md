---
title: "Can't get terminal to open."
date: 2007-06-04
forum: General Help
---

### Post by huckleberrymopo3 on 2007-06-04
I've been working on getting dual monitors to work in 7.04 well I got it to work then I thought I'd like to try beryl with the 2 cubes feature, and now I can't get to terminal to change the monitor setup back to the way I want gksudo nvidia-settings
I have previously had problems opening terminal while using beryl, but I just switched back to the ubuntu default to do terminal work.

---

### Post by dfreer on 2007-06-04
Did you save the nvidia settings to /etc/X11/xorg,conf? for some reason I had this problem when I used sudo nvidia-settings to enable tv-out with xinerama. A temporary terminal can be found with <Ctrl><Alt><F5>, or you can try running the command with <Alt><F2>
I'm still working on why nvidia prevents terminal (and I think gedit although I'm not for sure) from opening.

make sure to backup your /etc/X11/xorg.conf files everytime you edit them!

---

### Post by huckleberrymopo3 on 2007-06-05
I tried crtl+alt+F2 but it doesn't work. I believe it needs to GUI. I think I'll look to reconfigure X and redo the nvidia stuff. though im still confused as to why beryl has similar issues. thank you for your help.

---

### Post by huckleberrymopo3 on 2007-06-05
I reconfigured Xorg with sudo dpkg-reconfigure xserver-xorg (pressed enter 20 times) and now im back in business and terminal works great. thats for your time and help.

---

