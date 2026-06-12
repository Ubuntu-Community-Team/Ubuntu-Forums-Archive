---
title: "Random green pixels??"
date: 2014-11-17
forum: General Help
---

### Post by Arbiter on 2014-11-17
Hello all,

About a year ago, I built a new computer to run Ubuntu.  I have had zero problems with it until about mid last week.  I have changed none of the hardware and for whatever reason, certain images and program windows or title bars have randomly occurring little green pixels scattered around.  They change position when a window is moved or refreshed.  It has become a nuisance and I believe it is spreading - images on websites have now become practically un-viewable because of these green pixels showing up.  They move around rapidly if there are animations of any kind.  Anyway...

Here's my hardware specs if it helps:

CPU: AMD A10-6800K "Richland" APU
Motherboard: Asus F2A85-M PRO - AMD 85X (Hudson D4) Chipset, Socket FM2
RAM: 8GB (2 x 4GB) DDR3 1866 RAM (G.Skill Ripjaws X)
Hard Drive: Seagate 2TB NAS HDD SATA 6GB/s
Video: APU-Integrated Radeon HD 8670D

All of this running Ubuntu 14.04.1 LTS 64-bit Desktop.

Anyone ever encounter this or have any thoughts?  I'm just hoping there's nothing wrong hardware-wise. :(

Any help would greatly be appreciated.

Thank you and best regards,

Arbiter

---

### Post by Arbiter on 2014-11-17
Anybody? :(

---

### Post by Thee on 2014-11-17
That happens to me sometimes when my computer is in Suspend mode and when I bring him back from suspend. Green pixels show up randomly on the top side of the screen. But it also goes away after some seconds. Its like the graphics card is still not fully initialized after suspend or something.
Really can't tell you much more about it. Maybe it got something to do with Radeon drivers (as I see that you have Radeon too, like me), otherwise can't really help you.

---

### Post by Arbiter on 2014-11-17
Thank you for replying to me.  I'd have to agree- may be something to do with Radeon drivers, as I have tried switching from the open source Radeon driver to the proprietary ones without affecting the issue.  Also tried running AMD's latest drivers from their website, also without result.

Maybe I just should do a fresh install and hope for the best. :(

> **Thee said:**
> That happens to me sometimes when my computer is in Suspend mode and when I bring him back from suspend. Green pixels show up randomly on the top side of the screen. But it also goes away after some seconds. Its like the graphics card is still not fully initialized after suspend or something.
Really can't tell you much more about it. Maybe it got something to do with Radeon drivers (as I see that you have Radeon too, like me), otherwise can't really help you.

---

### Post by Thee on 2014-11-18
So it never goes away on your computer?
For me it goes away after 2-5 sec. Maybe mine and your problem are not related... did you try cleaning your graphic card and cpu cooler from dust?

---

### Post by Arbiter on 2014-11-20
> **Thee said:**
> So it never goes away on your computer?
For me it goes away after 2-5 sec. Maybe mine and your problem are not related... did you try cleaning your graphic card and cpu cooler from dust?

For me it is persistent.  I keep my computer very clean- I dust it out once every couple weeks.  Not sure why this would happen...starting to think maybe there's some conflict with the built-in Radeon graphics and a kernel update or somesuch.  I'm going to attempt a fresh reinstall tonight to see if that helps.  :-/

---

### Post by mardy3 on 2015-05-22
I also have the same issue, with a radeon R5 240. It seems to only affect the Ubuntu background so far, and only from time to time.
It goes away if I open the System Settings -> Displays and then I set a lower resolution. Then I set my previous (max) resolution back, and the green flickering pixels are no longer there.

---

