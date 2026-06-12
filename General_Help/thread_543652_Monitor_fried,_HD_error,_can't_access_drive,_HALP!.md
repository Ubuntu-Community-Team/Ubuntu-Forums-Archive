---
title: "Monitor fried, HD error, can't access drive, HALP!"
date: 2007-09-05
forum: General Help
---

### Post by Skeorx13 on 2007-09-05
The computer I built for my roommate is repeatedly getting screwed up. First the hard drive stopped working. (bios recognizes it, OS recognizes it, but I can't access it in ubuntu at all, refuses to fully mount. Something about a bad superblock.) And now his LCD monitor is broke. The monitor is maybe a year old only. When the system starts the monitor flickers and displays for only a split second and then blacks out. Whenever the screen changes display modes (startup, loading OS, bios, etc) it displays the proper info for a split second and dies again. The monitor controls don't respond at all, and when the computer is off but the monitor is still on it shows no menu or "no source" mini screen at all like it used to. I figured this meant that the monitor was messed up and not the computer itself. I hooked up an old CRT monitor and it worked fine. So the only thing I can think of is the lighting source behind the screen might be fried, or possibly some capacitor or something isn't firing properly. I don't recall the name of the monitor off the top of my head but I can update this thread when I get home today.

If anyone also knows of a program or procedure to fix the HDD (at least for a short time period) I'd greatly appreciate any help with that as well. The drive is a 40 GB seagate (Barracuda I believe). If the drive is dead, it's ok, I can get a new one. But I do need to rescue a few gigs of data from it. I can't boot from it. I had another computer with ubuntu on it and I just pulled the drive out and made it the master. Hooked the busted one up to slave and booted. (I just reconfigured the xserver to be able to boot into gnome) Ubuntu lists the drives properly in nautilus but when I try to access the bad drive I get this error: 
> Mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error in some cases useful info is found in syslog - try dmesg | tail or so

---

### Post by ajgreeny on 2007-09-05
Have you tried adding the dead? drive as slave to a winXP machine and installing a prog that will read and copy or even allow all read and write access to linux drives.  I don't know if it will work but it must be worth trying.

---

### Post by Skeorx13 on 2007-09-05
That was going to be my last step if it doesn't work in the linux system. I have xp dual booted on mine, but I wanted to exhaust my options lest my roommate's bad luck infect my system too. lol

---

