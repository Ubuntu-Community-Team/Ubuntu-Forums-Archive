---
title: "printer will not print in java terminal"
date: 2007-05-07
forum: General Help
---

### Post by thomasbaker on 2007-05-07
To access my company work order database, I connect through webconnect, from a website. This launches a java based terminal to access my work orders.  I need to print these work orders. If I hit print the printer shows up in my system tray. But thats it nothing.  If I look at the print jobs spooler and it says stopped.  This printer works just fine with any other application. I have a hp 812c. Im using fiesty, all updates installed.  If I access with winblows  they print just fine.  Please help me with this pain in my rear. I am sick of dual booting.

This is want the cups error log says after trying to print page.

E [07/May/2007:19:38:58 -0500] [Job 16] No %%BoundingBox: comment in header!
E [07/May/2007:19:38:58 -0500] [Job 16] No %%Pages: comment in header!
E [07/May/2007:19:38:59 -0500] [Job 16] /configurationerror in --setpagedevice--
E [07/May/2007:19:38:59 -0500] PID 16604 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!

thanks
thomas

---

### Post by abc123456 on 2007-05-08
The cups filter is bad.  sudo apt-get install lprng magicfilter set it up for network printer.  When sudo magicfilterconfigure the third line put the ip nimber ie. 193.134.1.20 it will use that printer.  The next line sets the filter chose the one for the network printer.  System Admin should help. Ask.:popcorn:

---

