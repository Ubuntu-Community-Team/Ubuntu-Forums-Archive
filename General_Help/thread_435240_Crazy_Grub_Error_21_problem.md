---
title: "Crazy Grub Error 21 problem"
date: 2007-05-06
forum: General Help
---

### Post by Hoozer on 2007-05-06
So I have kind of a different style error 21 problem. I've had two hard drives for about a year, and about 3 months ago I put linux on my Seagate Sata 300gb, my other hard drive is a Western Digital 160 gb IDE hard drive. I used to dual boot with one having windowsXP pro, and Windows Home. I cleared the SATA which had windows XP pro and but Ubuntu 6.10 on it. Everything was fine and then I started getting GRUB error 21 messages out of nowhere. I checked my BIOS and everything and I set my hard drive detections to automatic (which I hear is a common fix). The weird thing is if I would leave my computer alone for a little while sometimes it would be fine and start up no problem. Now it does the GRUB error 21 all the time and I can't boot into either windows or linux. I thought maybe one of my hard drives was dying, so I took it out (the linux hard drive on the SATA 300gb), but I still get the error 21 message. Does God hate me? What the heck is the problem with my system?

---

### Post by Hoozer on 2007-05-09
A friend that I talked to about this problem suggested that maybe my mother board was dying/dead, can anyone confirm this?

---

### Post by confused57 on 2007-05-09
Maybe you can install Window's IPL code to the Window's drive mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
if you have trouble booting your Window's drive, then it could be a hardware problem

You can always reinstall grub with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Think maybe your SATA cable is faulty?  There could still be a problem with your Ubuntu drive, by taking it out the grub IPL code on your Window's drive can't find grub on the root partition, which it needs to boot.

---

### Post by Hoozer on 2007-05-11
The thing that confuses is me is that this is a gradual decline type thing. I used dual booted ubuntu and windows fine for months. It's only somewhat recently that the problems started. It seems weird that the software would somehow find a way to screw itself up.

---

