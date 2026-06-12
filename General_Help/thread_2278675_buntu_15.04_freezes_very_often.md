---
title: "*buntu 15.04 freezes very often"
date: 2015-05-18
forum: General Help
---

### Post by jicha on 2015-05-18
Hello,

I upgraded from Kubuntu 14.10 to 15.04 and since then I have a lot of problems with system completely freezing. My computer is a Shuttle XS35V4 with Celeron J1900 (Bay Trail) chipset.

I thought it might be because of Plasma 5.x and switched to Xubuntu (I did a clean new installation) but it freezes too. I have no idea what might cause it. It freezes randomly with no clear pattern. I use the computer as HTPC so mainly it happens during watching a movie or live TV (DVB-T). But even if I leave the computer with just desktop and no running applications, after I come back it is usually frozen.

I have no idea what might be causing this. I can not do anything else then shutdown the PC with HW button and start it again. I didn't have these problems with 14.10 version.

What could I try to identify the problem and possibly fix it? I suspect graphics or WiFi drivers but I have no proof that they are the root cause.

---

### Post by dino99 on 2015-05-18
plasma5 still have some issues not fixed yet with xubuntu; and request more ram than the previous version. So i cant say if your celeron is able to run it smootly, and if you have enough free ram

---

### Post by RobGoss on 2015-05-18
One of the biggest problems to cause a system to run slow is not having enough ram especially on a older machine or a  graphic  that does not meet the requirements.   

Everyone knows that some light weight Linux distributions require very little ram minimum 512- in most cases, but even this amount will not give you the fastest running machine. With that in mind you might want to see how much ram you're machine has and maybe add more.

---

### Post by jicha on 2015-05-19
Thank you for the answers. Maybe I was not clear with the problem I have. The computer isn't slow. It runs smoothly. The CPU is 4-core 2,4GHz with 2GB RAM. It has enough power for my needs. But the system sometimes suddenly freezes. I mean it gets stuck completely. Screen freezes and PC won't response to keyboard, mouse or shutdown/log off button.

---

### Post by Patrik_Mattsson on 2015-05-28
It's a bug with the Intel Graphic driver, the current solution is to disable RC6 (read the links to find out more)

[https://bugs.freedesktop.org/show_bug.cgi?id=88012](https://bugs.freedesktop.org/show_bug.cgi?id=88012)
[https://github.com/OpenELEC/OpenELEC.tv/issues/3726](https://github.com/OpenELEC/OpenELEC.tv/issues/3726)

---

### Post by RobGoss on 2015-05-28
It's really hard to pin point what's causing the freeze up. It might be something in the newer version that does not correspond with the specs of your machine.

As Ubuntu increases it's flavors so does the demands to run it, it will use more ram and require better graphics cards.

A lot of our older machines does not meet this requirements but yet we run Ubuntu because we can.

---

### Post by jicha on 2015-05-29
Thanks a lot. This sounds like the bug I'm experiencing. I expected it is the graphics driver because it usually happened when playing a movie. And while KDE (just running desktop) was freezing very often Xfce never did.

I read through the discussions but unfortunately I didn't understand it fully. To disable RC6 I need to set it as an option when compiling kernel or can I disable it in a configuration file with stock kernel? I also read there that it could be fixed by some settings in BIOS. I will try it.

---

### Post by cblanquer on 2015-11-01
Hi 
Same problem here: Shuttle XS35 v4 (processor J1900 <=> i3 in my opinion, 8 Gb) with Ubuntu 15.04 (Kernel: 3.19.0-31-generic, runnning Unity). Most often while I am playing Megaglest.

This problem does not happen with XS35 GTA (processor D2700 and AMD graphics) nor in the former XS35 (processor Atom and Nvidia ION2 graphics), which I already have and use. Not found yet what causes it, most probably as mentioned before the Intel graphics driver.

Not tried yet to fix, have you got a solution yourself?
-----
I have read the email trails from [https://bugs.freedesktop.org/show_bug.cgi?id=88012](https://bugs.freedesktop.org/show_bug.cgi?id=88012) .
Comment 52 points to suspect an regression issue in the new kernels:

Juergen Froehler 2015-03-29 08:12:43 UTC
"mainline kernel between 3.13 -> 3.16 do not have the freeze issue
every mainline Kernel between 3.17.x -> 3.19.2 the freeze appear fast & frequently
mainline Kernel 3.19.3 (without legacy turbo fix) - rarely random freeze (I had just one in 4 days - still early to say more) but less as before
patched Kernel 3.19.x + legacy turbo fix - running rock solid = no freeze over long time period.
(...)
I had time to run the latest mainline Kernel 4.0.0-040000rc5.201503230035 during the last 2 days and my findings are that the freeze still exist."

The discusison continues until the day before esterday and seems to confimr a kernel issue as of varied configuraitons are described. :-(

---

### Post by jicha on 2015-11-02
As you can read in the bug description, the freeze is not fixed yet. All kernels after 3.16 are affected by this critical bug so the only solution is to use an old kernel.

---

### Post by cblanquer on 2016-03-23
I upgraded yesterday to 15.10 , kernel 4.2.0-34-generic.
The freeze happens even more often. Sounds like actual bad news.

---

### Post by oldos2er on 2016-03-23
Since this thread references a version of Ubuntu that is no longer supported (15.04), closing.

Anyone on 15.10 having similar problems, please start a new thread.

---

