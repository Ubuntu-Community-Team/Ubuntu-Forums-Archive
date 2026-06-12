---
title: "Multi-Boot Choice-Need Recommendation"
date: 2007-05-01
forum: General Help
---

### Post by HKTZONE on 2007-05-01
I am a long term user of Win XP and tired of all the breakage it has. I've downloaded Ubuntu 7.04 to see if I should take the leap. I have little technical skills with Linux and the Ubuntu implementation. 

This is my basic setup: 
Dell Inspiron 8200 Laptop (2ghz)
 - 60GB Hard disk (25G Available)
 - 1.25GB Memory
 - The usual MS Office Apps
 - IE 6 + Firefox 2
 - Win XP sp2
 - DLINK Cable Router to Internet and Wire + Wireless local LAN
 - Cablevision ISP

I have a few  Questions:
 1. Can my Config support a Virtual environment that will handle both WinXP and Ubuntu 7.04?
 2. Which Virtual OS do you recommend?
 3. If a Virtual OS will give me more then just a little performance hit then, which Multi-Boot manager would be best and easiest for me to install?.

---

### Post by Jonathan123 on 2007-05-01
If Windows "breaks" too much for you, you shouldn't be using Linux. :lolflag:

---

### Post by jackn on 2007-05-01
> **HKTZONE said:**
> I am a long term user of Win XP and tired of all the breakage it has. I've downloaded Ubuntu 7.04 to see if I should take the leap. I have little technical skills with Linux and the Ubuntu implementation. 

This is my basic setup: 
Dell Inspiron 8200 Laptop (2ghz)
 - 60GB Hard disk (25G Available)
 - 1.25GB Memory
 - The usual MS Office Apps
 - IE 6 + Firefox 2
 - Win XP sp2
 - DLINK Cable Router to Internet and Wire + Wireless local LAN
 - Cablevision ISP

I have a few  Questions:
 1. Can my Config support a Virtual environment that will handle both WinXP and Ubuntu 7.04?
 2. Which Virtual OS do you recommend?
 3. If a Virtual OS will give me more then just a little performance hit then, which Multi-Boot manager would be best and easiest for me to install?.

HKTZONE, checking out Linux is an excellent idea, IMHO.
I don't know much about virtualization, just look at the requirements of the various VM's. My guess is you have a good enough machine.
The main point I'd like to make is that it's a good idea to have dual-boot in any case. It's not such a hassle to switch between the OS's, and there are advantages: 
a. if sth goes wrong in one OS, you can test your hardware on the other, that way telling hardware and software problenms apart. 
b. You always have a backup system in case of a major SNAFU. It's almost like having two boxes. That's extremely important in case you lose your connection to the net on one OS.
c. No loss of performance.

GRUB does the job for me, but I only dual-boot.

Jackn

Jackn

---

### Post by Turellius on 2007-05-01
I have a few questions for you.  You do realize that once things are running good, and everything is installed that Ubuntu is very nice, but that a decent amount of configuration is needed, not to mention that most things are not idiot-proof as they are in Windows?  If I was you I would not mess with virtual machines.  If you want to test Ubuntu out, use it as Live CD (pop it in and reboot).  This will give you an idea what it is like.  If you like it then just install it.  You don't need a 'Multi-boot manager'.  Yiou can use the partitioning utility that is included on the CD to resize your current partion and create a new one.  Don't forget to set a mount point in the partition and also create a 'swap' partition.  It should automatically create an boot list so you can select either Ubuntu or your Windows OS.

---

