---
title: "My game runs very slow on Xubuntu"
date: 2020-08-20
forum: General Help
---

### Post by johnvs99 on 2020-08-20
Hi! I recently used my laptop again, which has Xubuntu installed. The PC has these characteristics:
HP Pavilion dv6700 Notebook PC (FE838UA # ABA)
CPU: Intel (R) Core (TM) 2 Duo CPU T5750 @ 2.00GHz
Architecture: 64 bit
RAM: 3GB
the graphics card I think is:
Intel Mobile GM965 / GL960 Integrated Graphics

What happens to me is that I am developing a small video game in java. I use the OpenJDK and the Eclipse IDE. When I run the video game, if the PC mouse is still then the game runs very slow, but while I continuously move the mouse the game runs at normal speed.. I don't know why this is. By the way, in Windows 10 I don't have this problem because when I run the game in that operating system it runs perfectly.

If anyone helps me with this problem I would appreciate it.

---

### Post by TheFu on 2020-08-21
So people know what you are working with: [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core2+Duo+T5750+%40+2.00GHz&id=989](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core2+Duo+T5750+%40+2.00GHz&id=989) about 700 passmarks.

I'd suggest checking that all the drivers are correct, assuming $100 for a much faster computer is too much.
No way would I upgrade that system for even $10. The 2008 integrated GPU is the worst part and cannot be upgraded in a laptop.

A used Chromebook from 2013 would be over 2x faster, have a much better iGPU, much longer battery, and support vt-x.  

Decision comes down to how much is your time worth per hour to solve this?  Times are difficult, so many of us don't have $85 for a replacement, faster, used, laptop/desktop. 
If you have $220 and an existing desktop, the jump into 13,000+ passmarks is possible with a MB+CPU+RAM upgrade.  I've been looking at a system like that for over year, waiting for the price to drop into the $180 range for an upgrade. No hurry.

Sorry - left out the main idea - switch to Wayland from X11 as the display manager. For non-remote window programs, it should be faster.

---

### Post by johnvs99 on 2020-08-23
Thanks for giving me an answer, I will see how I use the information to solve my problem.

---

### Post by TheFu on 2020-08-24
[https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop](https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop) 
How to enable/disable wayland.

---

### Post by Yellow Pasque on 2020-08-24
> **TheFu said:**
> I'd suggest checking that all the drivers are correct, assuming $100 for a much faster computer is too much.
No way would I upgrade that system for even $10. The 2008 integrated GPU is the worst part and cannot be upgraded in a laptop.

You seem to assume this is a general performance issue. Based on description, I think that's a bad assumption. The performance seems okay as long OP is moving mouse, so that would suggest some sort of issue with OpenJDK not redrawing/refreshing screen unless mouse is moving.

---

### Post by TheFu on 2020-08-24
Java has all sorts of issues and always has, especially with desktop applications. There are many good reasons why enterprises don't use Java for desktop programs, only back-end server stuff.

I was trying to stay away from my personal opinion that java sucks and should always be avoided if there is **any** other option.  I'm amazed that the OP is running eclipse with only 3GB of RAM on a 700 passmark computer. That has to be painful. i've done java development on a Core i5 with 8GB of RAM using Eclipse and wanted to kill myself during and after doing that. I'm joking, but it was the worse, by far, experience in my programming lifetime.  I was doing Fortran on a TRS80 with 1 floppy drive. A "Hello World" compile took 45 minutes, then another 45 minutes to link.  Eclipse on my Core i5 was worse (subjectively speaking), because my expectations had changed in 25 yrs.  Eclipse is like trying to startup iTunes AND Outlook on the same under-powered Windows PC concurrently - painful.

I was trying to avoid my anti-java experiences.  Now, I'll need to meditate an hour to get back to my happy place. ;|

Hopefully, Wayland made everything faster.

---

