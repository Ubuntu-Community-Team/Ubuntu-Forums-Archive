---
title: "trying to set up two monitors with randr"
date: 2018-04-20
forum: General Help
---

### Post by bubblefish2 on 2018-04-20
hey. when I am trying to setup one or two monitors, I get nearly always this error

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  34
  Current serial number in output stream:  35


sometimes I dont get this, and both monitors start to work seemingly magically and all is fine. this happens usually when I have played around with arandr for like half an hour, and suddenly dont get the error anymore. if I change settings from arandr, the problem usually returns. I really have no idea what connects these cases when it wants to decide work properly, and when not. I have tried to find that error code, opcode and whatnot with google, no success. and btw screensize is not the problem here, I have set it big enough.

I am still pretty new to linux and learning allot, if you could push me to right direction at least with this problem, Id appreciate it allot. thanks in advance.

edit1: I found out that if I put the monitors to overlap each other slightly, and position one of them to top right corner of screen-space, and another one to left bottom corner, it works 100% of time without error. I still wanna "fix" this cos I wanna learn, anyone have any ideas what might cause these errors?

---

