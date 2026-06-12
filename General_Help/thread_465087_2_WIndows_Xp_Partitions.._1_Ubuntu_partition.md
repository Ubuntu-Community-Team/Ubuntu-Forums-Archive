---
title: "2 WIndows Xp Partitions.. 1 Ubuntu partition"
date: 2007-06-05
forum: General Help
---

### Post by Eric the Red on 2007-06-05
Currently I have a dual boot with windows Xp and Ubuntu. However, our school is making us use an application that's used on Xp (which is breaking my xp partition) because of this I need to know if I can have 2 partitons of XP (one that's stable and the other one with the application that I messes up my computer)  and then install a copy of Ubuntu over everything. Please let me know if this is possible. Maybe even if I can run Windows XP in a Virtual Machine? I've heard of people doing this to combat my problem, but have no idea how it works.

---

### Post by bmeyer on 2007-06-05
What is the software that they're requiring?  Is it something that can run in WINE?

---

### Post by Eric the Red on 2007-06-05
Nope its called "System Architech" and requires a secondary key validation program.. so that would be entirely out of the question.

---

### Post by bmeyer on 2007-06-05
Am I right in guessing that the dual boot is only on one hard-drive instead of having dedicated drives for each?

---

### Post by viciouslime on 2007-06-05
> **Eric the Red said:**
> Currently I have a dual boot with windows Xp and Ubuntu. However, our school is making us use an application that's used on Xp (which is breaking my xp partition) because of this I need to know if I can have 2 partitons of XP (one that's stable and the other one with the application that I messes up my computer)  and then install a copy of Ubuntu over everything. Please let me know if this is possible. Maybe even if I can run Windows XP in a Virtual Machine? I've heard of people doing this to combat my problem, but have no idea how it works.

Both your suggestions are possible. The virtual machine will be easiest. However, if you want to install 2 copies of XP to two separate partitions, install the first as you normally would, the when you install the second just install it to the second partition when you're in the text-based part of the install. You can even use the XP installer to create the partitions. This will give you a system with a boot menu showing two different copies of XP.

Next install ubuntu, it will add both XP installs to grub so then you will have XP XP and Ubuntu. Beware however, it is best to have a separate home partition in Ubuntu, doing this here though means you will have 5 partitions, XP1, XP2, ubuntu root (/), ubuntu home (/home) and swap. You can't have 5 primary partitions so you would need to put some of them as logical partitions. I don't think XP can boot from a logical partition so Stick ubuntu in one.

Another warning would be that to do this you'll need two XP licences.

---

### Post by dgkulzer on 2007-06-05
I have 2 XP partitions on my computer and 1 ubuntu partition. I have one main XP partition and one XP partition thats just used for games along with one ubuntu partition. I did this because some of my games security features do not play nice with dvd burning software and I dont want to get rid of it and then reinstall it all the time.

Anyway, all I did was install my 1st copy of xp.  When I installed it I used the install cd to partition my hd, I maid a partition for this copy of XP and also a partition for the second copy of XP.  After installing it I installed my second copy of XP onto the other partition I already created.   When I was all done with this I installed Ubuntu 7.04, which I put on its own seperate HD.  Everything works great so far.

---

### Post by linux noooob on 2007-06-05
ya you can have two windows xp partitions (i do) but i would suggest lowering a partition so there is some free space on the actual hard disk and install windows to it.

ps. this may sound noobish but how do i post a thread?

---

