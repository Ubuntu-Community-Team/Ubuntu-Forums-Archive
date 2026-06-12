---
title: "Random apps suddenly taking up 4 GB of memory"
date: 2008-02-10
forum: General Help
---

### Post by Ebuntor on 2008-02-10
Hi everyone,

For some reason completely random applications suddenly take up 4 GB of memory, according to the system monitor. I don't even have that much memory but my system does get very slow when this happens. It can happen to any program; synaptic, firestarter even just a terminal even while they're idle. At times there can even be multiple programs taking up 4 GB (totaling 16 GB of memory).

I have no idea why it's specifically 4 GB or why it happens to a certain program. I run the 32-bit version of Ubuntu and as I understand it that version doesn't even support more than 3 GB. Could an important setting have changed without my knowing? I also should add that only the system monitor indicates it's 4 GB, according to conky it's just normal memory usage. 
It suddenly started a few days ago.

Anyway I can fix this? 

Thanks in advance

---

### Post by Ebuntor on 2008-02-10
I think I just found one commonality between those programs, all of them use sudo. I noticed that when I started a terminal and as soon as I entered "sudo <command>"  memory usage jumped from 5,7 MB to 4 GB.

So maybe there is something wrong with the root account's memory usage settings? (Just a guess of course, I have no idea)

---

### Post by Ebuntor on 2008-02-10
It's not entirely correct that only programs using sudo use 4 GB, also a few non-sudo apps like an AWN dock applet. Also not all but only certain  4 GB programs make my system slow.

If found out that only the Gnome System Monitor indicates that there's so much memory usage.

Seems like there isn't very much logic behind this, at least I can't see any.

---

### Post by Ebuntor on 2008-02-11
*bump*

---

### Post by Tamale on 2008-02-12
I have this problem too, but for me it's really only happening with firefox and xgl.  I can watch the usage go from 4mb, to 8mb, to 15mb, then suddenly it just jumps straight to 3.8, 3.9, or 4.0GB.  My system too runs quite slow when this happens and the swap space is shown as almost totally full.

I run 32bit gutsy with compiz on an hp nc8430 laptop.. core 2 duo 2.0ghz, 2.0gb of ram, x1600 pro, 100gb sata hard drive.

This is very annoying!  Please assist!

---

### Post by Ebuntor on 2008-02-13
> **Tamale said:**
> I have this problem too, but for me it's really only happening with firefox and xgl.  I can watch the usage go from 4mb, to 8mb, to 15mb, then suddenly it just jumps straight to 3.8, 3.9, or 4.0GB.  My system too runs quite slow when this happens and the swap space is shown as almost totally full.

I run 32bit gutsy with compiz on an hp nc8430 laptop.. core 2 duo 2.0ghz, 2.0gb of ram, x1600 pro, 100gb sata hard drive.

This is very annoying!  Please assist!

Hmm, I think your problem is somewhat different than mine. My programs don't use any extra swap.  I dunno what the problem really is but for some reason the Gnome system monitor is the only monitor which indicates this high memory usage.

---

### Post by Tamale on 2008-02-16
> **Ebuntor said:**
> Hmm, I think your problem is somewhat different than mine. My programs don't use any extra swap.  I dunno what the problem really is but for some reason the Gnome system monitor is the only monitor which indicates this high memory usage.

Not hard swap usage, just the indication that memory is 'in use' by programs.  I'll post a screenshot when I see it again in a couple weeks.. could you do the same?

---

### Post by JKyleOKC on 2008-02-18
This may be similar to my problem: anything that uses gksudo will freeze the system for almost exactly 30 seconds, with the whole screen going slightly darker during that time as soon as I finish entering my password on the GKSUDO dialog. It then un-freezes and everything is normal again until the next time I have to go thru gksudo.

It started immediately after I upgraded from Fiesty to Gutsy; had to do the upgrade so that both saned and vmware would work on that box. I'm using Xubuntu and the system is an ancient Gateway with 256 MB RAM and a Pentium III CPU.

Using Fiesty, I had to use a special compiled kernel in order for saned to be able to scan, and that kernel didn't have the necessary modules for vmware to work, making it necessary to reboot to a different kernel to use virtual machines. When I heard that Gutsy had solved the scanner problem I did the upgrade, but it's been a bit of a headache (screensaver and other xorg issues as well). Now all seems good except for this 30-second lockup. Could it be something having to time out when trying to access some of the new security stuff?

---

### Post by Tamale on 2008-02-21
i'm afraid i never use gksudo :[

---

