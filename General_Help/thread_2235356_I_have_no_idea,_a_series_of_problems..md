---
title: "I have no idea, a series of problems."
date: 2014-07-20
forum: General Help
---

### Post by bravidonatir on 2014-07-20
I have, a series of problems with my laptop. I changed my update download mirror, to something a little closer to my location to make updates download faster, and then shortly after, I just decided to change it back to US Main Server. A little while after that, I go to use my computer again and then.... My USB ports don't work, my wireless card isn't functioning, I plugged in an ethernet and it still said I wasn't getting any internet. I try to go into UEFI and change the boot order to reinstall OS, but again, USB isn't working. SD cards never worked for me on Linux, anyway. My mouse (USB) isn't working. Nothing is working except the touchpad built into the laptop, and the keyboard. I tried to use the terminal for some tasks to see if I could fix it that way and it said I wasn't the root user. System monitor said CPU usage is fairly high, despite the fact I'm not doing anything on the laptop, as nothing is working. I didn't bother with the webcam, as that doesn't really seem essential to my problem. Any ideas, anyone? I have no freaking idea as to what could cause this. All I managed to do was reset UEFI to factory settings and then put the fast BIOS mode and secure boot off, then change the boot mode to CSM OS. Beyond that, I don't know where to start.

---

### Post by slooksterpsv on 2014-07-20
Can you get into GRUB and try booting into an older kernel?
Try running uname -a and what kernel version does it say?
```

shawn@shawn-Satellite-C75D-A:~$ uname -a
Linux shawn-Satellite-C75D-A 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by bravidonatir on 2014-07-22
It says kernel 3.13.0-30 #55 Ubuntu SMP.

---

### Post by ian-weisser on 2014-07-22
> **bravidonatir said:**
> My USB ports don't work, my wireless card isn't functioning, I plugged in an ethernet and it still said I wasn't getting any internet.

Hardware issues *before* boot may or may not indicate a UEFI issue.
Hardware problems *after* boot usually indicate a kernel issue.

From your description, mucking about with UEFI will probably not help you.
As slooksterpsv correctly advised, use the GRUB prompt to boot into a kernel older than the non-working 3.13.0-30.

---

### Post by slooksterpsv on 2014-07-22
Try modifying grub and added to the end of the line where it says quiet add:
noapic

---

### Post by bravidonatir on 2014-07-24
Booting into an older kernel seems to resolve all the problems except for being able to boot from a USB. I was having some trouble booting into GRUB, given the system came with Windows 8, which I uninstalled. I didn't know that you need to hold the shift-key.  Thank you for helping me guys :), sorry it took so long to respond. Work and whatnot :/

---

### Post by oldfred on 2014-07-25
In my old BIOS system default was USB ports off. So updating BIOS or resetting to defaults turned off USB ports. I had a few other settings and do not easily remember all of them, so I took photos of every BIOS screen. New UEFI systems have many more screens & settings. 
Check for USB related settings. But some have some settings that do not seem related but may be the issue.

For example this thread mentions with all Haswell Intel chips (at least with Dell) you have to enable Legacy boot for back light to work even when booting in UEFI mode? How that is related is unknown.

---

