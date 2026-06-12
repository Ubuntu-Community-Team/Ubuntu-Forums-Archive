---
title: "Why is XORG using so much cpu% ?"
date: 2007-11-23
forum: General Help
---

### Post by justinclark on 2007-11-23
Ok I have been experiencing some sluggish Gutsy issues.  When running the top command I can see that Xorg uses around 35% cpu with nothing running.  When I open Opera or Firefox Xorg stays around 75%.  I have read similar threads but I didnt find any direct solutions.  I am new to Linux and would greatly appreciate some help.  I have a DEll Latitude laptop D600.  20Gb hard drive, 512 mb mem, 1600Mghz Pentium M, and I believe an ATI Radeon something.  My friend did the Ubuntu install so I honestly dont know if I have the right driver for it.  Any help?

---

### Post by justinclark on 2007-11-23
Also, I have difficulty playing videos such as on Youtube.  They download just fine but play very choppy.  I never had this prob with XP.  ?????

---

### Post by disturbedite on 2007-11-23
my Xorg is only using about 3.5% of cpu, but then again i'm on kubuntu hardy & i'm not using compiz fusion.  but something may be up with your Xorg.

check that you don't have any apps that use or rely on Xorg specifically running with your task manager.

---

### Post by wnwek on 2007-11-24
I am having the same problem, and co-incidentally, almost the same laptop configuration (Dell Latitude D520, Intel Centrino Duo, 512 MB RAM, etc.). I have been wondering about the CPU usage thing myself for a long time, especially when I am using Firefox. It is kind of disturbing to see my sensor applet to shoot up to the high 50s in CPU temperature.

Any ideas why this might be happening? I am not using Compiz; in fact I had uninstalled Compiz, just to make sure it was not running as a background process, but it had not made much of a difference. 

I have noticed my CPU usually overheats when Firefox is running; I have a vague notion that it could be the webpages with flash in them (e.g. youtube, gmail with chat, etc.). Am I right?

Also, I have an NTFS partition which has a rarely used WinXP installed on it, but I keep a lot of data on it, so I keep accessing the partition. Does that require a lot of CPU usage, especially while moving files back and forth?

Thanks in advance!

---

### Post by justinclark on 2007-11-24
Yeah Im experiencing the same issues with it overheating and firefox trips when I try to view a flash page.  I do have CompizFusion installed but I know thats not the issue.  How do I look at the task manager?

---

### Post by Tyche on 2007-11-24
> **justinclark said:**
> Yeah Im experiencing the same issues with it overheating and firefox trips when I try to view a flash page.  I do have CompizFusion installed but I know thats not the issue.  How do I look at the task manager?

Use System Manager (It may need to be installed, but I don't think so) to view your processes.  As for your CPU usage, I'm on a Dell Inspiron 530N (it shipped with Ubuntu installed).  I noticed when I moved up to 7.10 that I had a LARGE drain on my system resources, and even slow-downs to the point of appearing that they were lockups.  I traced it to Tracker.  I have since disabled Tracker in every location I can find to do so, starting with System -> Preferences -> Sessions, and my CPU usage has dropped back to acceptable levels.  My personal opinion of Tracker is that it should be re-thought seriously, and certainly shouldn't be turned on by default.

---

### Post by yedidel on 2008-03-24
I have exactly the same problem with Dell Latitude D600 and ATI Radeon 9000.

I've tried disabling SpeedStep in BIOS, changing the SpeedStep module and nada.

I killed Tracker and it improved, although it may come back, and still FireFox when loading certain sites can reach 95% usage (FireFox and Xorg).

Using Gutsy 7.10, my first linux so I don't know what about other versions.
By the way, Dell released a SpeedStep Hotfix for Windows XP for the Dell latitude, it says that it fixed the problem that when the cpu gets to 100% it never comes down. I think it's the same problem (just there is no fix) in linux.

---

### Post by fragos on 2008-03-24
I found tracker to be generate more demand on my system than I wanted.  I replaced it with Google Desktop which in my case has minimal impact on system performance.

---

### Post by jsnelli2 on 2008-03-24
I believe it is an error with the ATI driver and xorg.  I had the same problem when I upgraded to the newest version of ATI's driver.  Compiz ran much better with the driver, but everything ran very slowly whether compiz was on or off.  I uninstalled the proprietary driver and everything is fine...compiz just doesn't run as smoothly as it should.

---

