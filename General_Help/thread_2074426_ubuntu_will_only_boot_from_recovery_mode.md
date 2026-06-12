---
title: "ubuntu will only boot from recovery mode"
date: 2012-10-21
forum: General Help
---

### Post by libbby on 2012-10-21
I installed a few new things on my laptop (salome and a fortran compiler so that I could set it up) and since then I cannot boot ubuntu normally. 

When I turn on my laptop I am given the option of loading ubuntu, ubuntu from recovery, previous linux versions etc. ubuntu will show me the loading screen but then turn to black, which is also what happens when I try previous linux versions. 

So I tried instead running in recovery mode through which I tried the file check, dpkg, and updating grub. When I selected resume I could log in, and from that I tried startx and gnome-session but it brought up a very ugly version of gnome in which half the things didn't work.

Is there anything I can do to go back to how it was before I decided to download things and try to break ubuntu?

---

### Post by kc1di on 2012-10-21
It sounds like the video or 3d got messed up somehow. 

when you get to the login instead of start-x or gnome-sessions try lightdm

that the windows manager for Ubuntu now (I'm assuming your talking version 12 here.)

---

### Post by libbby on 2012-10-21
Thank you for yoru quick response! When I try that I get a black screen with a blinking cursor and I can't seem to do much (I'm pretty new to linux incase that wasn't obvious!). What can I try from there?

---

### Post by libbby on 2012-10-21
and I am running Ubuntu 11.10 .. would giving up on this version and installing version 12 be the best option?

---

### Post by kc1di on 2012-10-21
I think 12 would be better my self. 
but if you want to try one more thing go to the following web page and download and run boot-repair see if that does it. 

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by libbby on 2012-10-22
When I am trying the boot repair it cannot download it. Also when I'm in ubuntu it seems it's not recognising that I'm connected to the internet. I think I've managed to mess something up pretty hugely!

---

### Post by kc1di on 2012-10-23
> **libbby said:**
> When I am trying the boot repair it cannot download it. Also when I'm in ubuntu it seems it's not recognising that I'm connected to the internet. I think I've managed to mess something up pretty hugely!

Sorry for the delayed answer:
At this point in may be best to re-install and you might as well jump to 12.04 also.
Good Luck.

---

