---
title: "k3b SLOW performance! Will this issue ever be solved?!"
date: 2007-05-27
forum: General Help
---

### Post by geo909 on 2007-05-27
Hello,

 I'm having (like so many other users) problems with k3b burning program.My DVD writer supports up to 8X burning but k3b doesn't perform up to 1-1.4X.What's going on?

 I search in Google and I see many other users asking the exactly same thing in forums and the replies are always like "yeah, me too", "hmm..I tried this but didn't work out" and it never ends somewhere...

 Will someone once and for all give a clear solution, step by step, so that anyone will be able to solve this problem?!

P.S. It's been 3 days since I switched from XP to Ubuntu and, while I'm amazed from the whole idea, I find very disappointing the fact that one has to be a computer geek to be able to do ordinary stuff like "fast" (or just descent) DVD burning..

---

### Post by kayosiii on 2007-05-27
from [http://www.quietearth.us/linuxburning.htm](http://www.quietearth.us/linuxburning.htm)

Question: Why does it write slow? 

 If you are using a regular ide drive (even with scsi emulation), you can use the hdparm command to check what more you are running in. If the using_dma parameter is not set, then you are running in PIO mode which is incredibly slow.
 
 Answer: Try enabling DMA mode with "hdparm -d1 [device]", but if this hangs the box or doesn't work, you're out of luck.
 
 # hdparm -v /dev/cdrom
 
 /dev/cdrom:
 IO_support = 0 (default 16-bit)
 unmaskirq = 0 (off)
 using_dma = 1 (on)
 keepsettings = 0 (off)
 readonly = 0 (off)
 readahead = 256 (on)

Turning on DMA really helps - generally K3B will complain if DMA is not on. You could also try tweeking the cache sizes and you could try different media.
It would also be helpful to know what model of burner you have.

My personal experience is that Linux(k3b) tends to burn disks a little bit slower than the media rating. However since I can do things like capture video at the same time as burning this doesn't faze me that much.

If you really really want faster burning you could also try Nero for Linux.

---

### Post by Shay Stephens on 2007-05-27
Maybe it's hardware?  I have a basic feisty install and use K3b to burn DVD disks and I can burn at 16x.  K3b has always worked great for me.

---

### Post by ramjet_1953 on 2007-05-28
I believe that there is a problem with Feisty, in that it uses a new driver in the kernel, that treats all drives as scusi.

That is all well and good, but apparently it has a problem with turning-on DMA.

Another reason why I will wait for a while before using Feisty.

It may be worth a look on the forums to verify this.

Regards,
Roger :cool:

---

### Post by geo909 on 2007-05-28
> 
Answer: Try enabling DMA mode with "hdparm -d1 [device]", but if this hangs the box or doesn't work, you're out of luck.

 Sorry for the noob question: how can I find out what's the name of my DVD in Linux( that is, [device]=?)? I put "cdrom0" but that doesn't work.

ALso, I tried some others:> ouga@ouga-desktop:~$   hdparm -v /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
ouga@ouga-desktop:~$ hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
ouga@ouga-desktop:~$ hdparm -v /dev/dvdrw

/dev/dvdrw:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

..but as you see, nothing works..

Also, my DVD writer model is: LITE-ON DVDRW SOHW-1693S
> Maybe it's hardware? I have a basic feisty install and use K3b to burn DVD disks and I can burn at 16x. K3b has always worked great for me.
 Well, lucky you! But the problem is not only mine..I see many others having the same.

 Anyway, for the moment, let's see how can I turn DMA on for my DVD drive...
(By the way, can that be potentially dangerous/harmfull or cause instability?!)

---

### Post by geo909 on 2007-05-28
Ok,
 while I was writting those lines, i was downloading the last updates.
Then I restarted my computer and everything got messed up: not only k3b now is not writing at all, but also the HD in which I have windows on is not being mounted on start up.Also some links doesn't work.
 What's going on for God's sake? I didn't do anything, just let Ubuntu update and thenI restarted my PC as I was asked to!

---

### Post by orb9220 on 2007-05-28
> I didn't do anything, just let Ubuntu update and thenI restarted my PC as I was asked to!

Look into the installation & upgrades forum.  Seems the latest kernel broke people systems.

When i had the update icon I right click prefs and set it to two weeks.  This gives them the time to rectify a bad or buggy kernel,restricted,xorg package. I do not need every aspect of my system to be updated daily. But that is just me.

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

And yes I also have a 16x burner with 16x media on my Nec 3550a and k3b sucks at burning media at the rated speed.
What doesn't make sense to me is the top window shows burning at 16x then the bottom actual shows 1x-6x never ever reaching 16x.

False Advertising?

I can right click burn iso or copy dvd in nautilus built-in burner at 16x and get a burned copy in 8mins top, But k3b takes 13-14 mins.

---

### Post by geo909 on 2007-05-28
Ok, so it was the Kernel's problem. The thing is that I'm a noob when it comes to Linux. When I see "Updates available", I don't know what's everything, I just download all of them.

 As for my problem, well, I don't know.I'm going to re-install Ubuntu and see if that's working. (By the way, DMA was on for my DVDRW.The problem was somewhere else)

---

### Post by Egils on 2007-06-01
I was having trouble with slow burn speeds as well but I found this info on the K3B website:

> Q: My DVD drive supports 16X but K3B keeps burning at 1X! What's happening?
A: Your kernel most likely didn't apply optimal settings for your drive when it detected it. You can find out what are the current settings of your drive with the command

hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

[B]The following options are known to maximize burning and playback performance:

hdparm -d1 -c1 -a8 -u1 /dev/dvd[/B]


After applying the hdparm command (with sudo) everything began to work properly, so it turned out that my problem was only related to the drive settings. 

This is a temporary solution however. For the changes to be permanent it's probably necessary to edit the hdparm.conf file and there is some info about this in the following thread:

[http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm+dvd](http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm+dvd)

---

