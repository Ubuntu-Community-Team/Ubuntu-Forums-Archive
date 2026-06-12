---
title: "Dell Inspiron 6000 Ubuntu 12.04 way TOO slow"
date: 2012-12-24
forum: General Help
---

### Post by shan2812 on 2012-12-24
Hi,

I installed 12.04 on my Dell Inspiron 6000, 1GB RAM, Centrino 1.6GHz, 160 GB HDD

But its incredibly slow! After clicking on Dash Home,I have to wait for more than 30 seconds for the window to appear!

I wonder if my hardware is insufficient for 12.04 or anything else could be wrong with my installation/confirgutaion(but I haven't done any changes after the installation), or should I use any earlier version of Ubuntu?(my usage is mainly browsing internet with wireless internet)

Any inputs would be appreciated.

Thank you

Cheers
Shan

---

### Post by ibjsb4 on 2012-12-24
Try the Classic desktop, see if its any better.  

sudo apt-get install gnome-session-fallback

And choose at login.

Also could be video driver.

---

### Post by 3rdalbum on 2012-12-24
If you have Nvidia or recent ATI graphics, install the driver from the Additional Drivers program.

Otherwise you can install Unity 2d to get a less graphically-intense desktop environment. Switch to it via the cog menu at the login screen.

---

### Post by 2F4U on 2012-12-24
Depending on which source you read, your system is below or barely meets system requirements for Ubuntu (with Unity). If I am not mistaken, your machine is kind of an old laptop, so don't expect wonders. Ubuntu with Unity can be quite resource intensive, but you might run Xubuntu or Lubuntu. I've been successfully running both on similar hardware.

---

