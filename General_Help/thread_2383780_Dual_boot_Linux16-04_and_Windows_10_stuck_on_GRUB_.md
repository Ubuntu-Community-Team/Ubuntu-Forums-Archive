---
title: "Dual boot Linux16-04 and Windows 10 stuck on GRUB RESCUE"
date: 2018-01-29
forum: General Help
---

### Post by s_m2 on 2018-01-29
Hi, I have had Linux working on this current hardware configuration for quite a while (first Linux 14.04 & Win7 and then now Linux 16.04  & Win 10). It has been working great until couple of days ago when I tried hard shutdown while in Windows 10 by pressing the power off until it shutdown. Now it gives me the dreaded GRUB RESCUE whenever I tried to start the boot process. 

I tried running the disk-repair utility and here is the file it generated and I can't make much out of it. I would really appreciate if someone can help me recover and get me going again with my Linux system (I don't much care for the Windows part of it, although ideally I would like to recover that too).

[https://paste.ubuntu.com/26466839/](https://paste.ubuntu.com/26466839/)

Thank you so much in advance.

Spatial

---

### Post by oldfred on 2018-01-29
What brand/model system?

You are not showing any Linux partitions.
And sda is only slightly referenced in report as this with no partitions or any data?

> usb-Brother_MFC-J870DW_BROK3F486757-0:0 -> ../../sda

Did you have Ubuntu on a USB drive?

It also looks like Windows fast start up or hibernation is on. Even if you turned it off before, Windows updates may turn it back on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by s_m2 on 2018-01-30
> **oldfred said:**
> What brand/model system?

You are not showing any Linux partitions.
And sda is only slightly referenced in report as this with no partitions or any data?



Did you have Ubuntu on a USB drive?

It also looks like Windows fast start up or hibernation is on. Even if you turned it off before, Windows updates may turn it back on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

This is a home brewed computer with Intel processor.

Both the Linux and Windows are on a hard drive and not on usb drive.
There are two hard drives (SATA) in this home brewed computer, and looks like it is showing the hard drive which does not have the OSes installed....the drive with the OSes is not showing up (AFAIK). Could it be that the hard drive is busted?

Thanks for your quick reply on this. I will follow up on the links that you provided and see if I get somewhere and in the meantime any further help by anyone is fully appreciated.

Spatial

---

### Post by s_m2 on 2018-01-30
OK...solved.... this turned out to be simple case of loose SATA cable connection to the hard drive containing the OSes....arghhhhh!!! I just panicked when I saw GRUB RESCUE and didn't think simplest of the things that could have gone wrong and was pulling my hair over it and ended up posting here to the forum. Sorry for all the troubles and I really appreciate folks who spent time reading and thinking over it and special thanks to ***oldfred*** for replying and trying to solve and work with me.

Great. Thanks again and I will mark it SOLVED.

Spatial

---

### Post by oldfred on 2018-01-30
Most of the SATA cables I have just plug in. But then saw some that have a locking tab, so now only buy those. But most drives do not come with the locking type.

I used to have similar troubles with the old PATA cables and I changed to SATA drives as soon as cost started to be close to PATA drives, hoping to eliminate cable type issues.

---

