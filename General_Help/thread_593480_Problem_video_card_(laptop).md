---
title: "Problem video card (laptop)"
date: 2007-10-27
forum: General Help
---

### Post by S1MAS on 2007-10-27
Hi,
I want create free linux ubuntu server (ftp, mysql, php&#8230;), but I have problem with my video card.
I use ubuntu 5.10 and ms windows xp.

My video card:
Company: Silicon Integrated Systems Corporation
Product: SiS 662_M662MX_M662
Software Version: 3.75
Driver Version: 3.75
Video Memory(Size): 128 Mbytes
Video Memory Clock: 200 MHz
BIOS(OEM ProductRev): 34201A
Video Bridge Chip Type: SiS 307LV Rev E1

I try comand: dpkg-reconfigure xserver xorg, but this not help:(

[IMG]http://ubuntuforums.org/g/images/397236/large/1_DSC00031.JPG[/IMG]

---

### Post by suchawato on 2007-10-27
You are using a much older version of Ubuntu.
There has been a lot of work done with regard to video card drivers since 5.10.
This may be related to a confirmed bug with regard to some older laptop monitor output problems in the kernel. Even though this is not a laptop, it may be related.
This problem is very possibly fixed in a newer version.
I had that snowcrash problem with an earlier version.
try upgrading to Gutsy, it has the best driver support. And they have done some work on that bug.

---

### Post by S1MAS on 2007-10-27
Can I get this linux for free to post?

---

