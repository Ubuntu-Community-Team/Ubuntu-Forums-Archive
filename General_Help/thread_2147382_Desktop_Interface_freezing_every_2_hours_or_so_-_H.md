---
title: "Desktop Interface freezing every 2 hours or so - How do I start Troubleshooting?"
date: 2013-05-21
forum: General Help
---

### Post by henrypootel on 2013-05-21
I'm using Raring on my laptop (Sony Vaio Z1), and i'm having a problem where after running for about 2 or 3 hours, the GUI will just freeze up.

I haven't been able to isolate it to a specific action or application, but it's consistently every couple of hours, and happens in Unity, Gnome (3.6 & 3.8), and Cinnamon.

The only way i'm able to get my system back is by doing the ol' ctrl-alt-f1 and restarting the lightdm or gdm service.

I'm typically running firefox, evolution, vmware workstation, an nautilus when this happens. my machine has an nVidia geforce 300m in it, and i'm using the proprietary 304-updates driver (310 seemed to crash a lot).

My question is: how can i start troubleshooting this problem? There must be a log os something somwhere which will help me identify what is failing.

I feel like it's the graphics card/driver that is the problem, but i have no idea how to confirm this or fix it.

This may be related, bu i've notice that quite often (about half the time), when i shut-down, it goes through the whole shutdown process, but just sits there showing the messaging saying that it has sent the shut-down signal or whatever, and is now shutiing down. i then just have to hold down the power button to turn it off, as it just never does it itself.

Any help would be much appreciated. My system details are:

Ubuntu Raring 64-bit, Sony Vaio Z1, Intel Core i7 2.26, 8Gb RAM, 4x64gb SSDs in software RAID0, GeForce 330m

---

### Post by ohnonot on 2013-05-23
you have given a lot of detail.
i am assuming that sth is taking 100% of your resources when this happens  - is it happening on different DE's but same install?
can you define  "gui freezes" further? can you still, e.g., open a terminal window via hotkey? then you could type "top" (or preferably htop, which you might have to install first) and it would show you what is taking up your resources. 
if that doesn't work, do the good old ctrl-alt-fX, login as root, and type top (or htop). or, login as user, and type sudo top|htop.

---

### Post by HiImTye on 2013-05-23
if you have access to another device, try SSHing into you box and running top/htop or checking ps

---

### Post by yiftah on 2013-05-26
Had a similar problem. Tried to backup my whole hard disk into an external device, using Nautilus. Everything froze after 10 - 15 minutes. I had to restart the hard way. Tried again and again. I also tried with no other app working - to no avail. Froze again. I tried to monitor the system. I was surprised that the cpu usage did not exeed some 50%. there was a lot of free memory as well. (but froze again..)

Finally I did the backup using old Dolphin.. which worked just fine
I am using a Ubuntu 13.04 on Samsung 305E laptop with AMD quad core. 

Yiftah

---

