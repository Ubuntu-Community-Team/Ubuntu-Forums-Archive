---
title: "[SOLVED] Trying to get system default back"
date: 2008-03-21
forum: General Help
---

### Post by wolfwood707 on 2008-03-21
So no offense to anyone but I'm trying to get rid of ubuntu (doesn't work with a bunch of my hardware apparently and I can't seem to fix that).

I've tried running my system disk and it comes up with "ERROR: No partion"

How do I fix this?

---

### Post by wolfwood707 on 2008-03-21
I got the partition editor everyone mentioned in other treads... I have no idea how to use it though.

---

### Post by aysiu on 2008-03-21
Can you please explain exactly what you're trying to do? Get rid of Ubuntu to what end? Are you trying to replace it with something else? If so, what? That information may help.

---

### Post by gaussian on 2008-03-21
> **wolfwood707 said:**
> So no offense to anyone but I'm trying to get rid of ubuntu (doesn't work with a bunch of my hardware apparently and I can't seem to fix that).

I've tried running my system disk and it comes up with "ERROR: No partion"

How do I fix this?

It would be useful to know to help you the following things:
1) What did you have? A dual-boot Windows (Vista/XP) and Ubuntu? Something else?
2) What have you done? Removed the Ubuntu install? How?
3) What do you mean by "running system disk"? Do you mean just booting up the computer?


My hunch (correct me if I am wrong) is that you had a dual boot system and now you have deleted the Ubuntu Partition. Now the Grub-bootloader that is still installed cannot find menu.lst from you /boot-directory since you have deleted the partition where it resides.

Solution to this: you need to install a bootloader. I think the simplest think is to use Windows installation media and run fixmbr (or something like that). I don't have Windows so I cannot check. After this boot and see if you can see if your Windows is working.

The next thing would be to use a Linux live-cd (your original Ubuntu installation media or the Gparted disk or something else) to resize your original Windows installation back to its full size. Before doing this back things up.

---

### Post by aysiu on 2008-03-21
Your subject title and subject content are confusing and seem to be at odds with one another.

*Trying to get system default back* sounds as if you screwed up Ubuntu somehow and want the default installation back.

*I'm trying to get rid of Ubuntu* sounds as if you want to install another Linux distro or Windows over it.

Please specify exactly what you're trying to do.

---

### Post by wolfwood707 on 2008-03-21
Sorry I was vague. Typing and holding a grabby baby make for short messages, heh.


I have Ubuntu installed still. I got the disks from the company I bought my laptop (Acer) to restore the factory defaults (Windows Vista). 

I tried booting from the first disk ("System Disk") as instructed. Came up with the 'no partition' error.

So now I've downloaded gparted, since it seems I need to partition the drive to run the System disk and the Recovery disk. (Still trying to figure out how to use gparted)

I figured: Partition the drive, run the disks, then try to get rid of Ubuntu.

If this is not such a hot way to do this, please let me know.

---

### Post by aysiu on 2008-03-21
With GParted (it sounds as if you've been able to run the program successfully--let us know if that's not the case), you should be able to delete the Ubuntu partitions altogether and then create a new partition for Windows Vista.

If you're unable to create an NTFS partition for Vista straight out, I believe you can create a FAT32 partition that Vista's installer can then convert to NTFS before installing.

My guess is that Vista's installer just doesn't know what to do with Ext3 at all. So go for FAT32 or NTFS.

---

### Post by wolfwood707 on 2008-03-21
gparted runs... but i can't get to the graphics mode. their website is really vague (hah) about how to get there.

---

### Post by wolfwood707 on 2008-03-21
nvm... got to the main screen (w/ graphics!)... now what?

(sorry... I'm new at this 'doing something with my computer besides surf the internet' stuff)

---

### Post by aysiu on 2008-03-21
Okay, what are you running GParted off of?

You can't run it off Ubuntu itself. You need to run a live CD (the Ubuntu Desktop CD will do) to delete the Ubuntu partition.

---

### Post by wolfwood707 on 2008-03-21
Running from livecd

here's the info:
(1)
Filesystem: ext3
Size 143.98 GiB
Flags: Boot

Path: /dev/sda1
Status: Not mounted

(2)
Filesystem: extended
Size: 5.06 GiB

Path: /dev/sda2
Status: Not busy (There are no mounted logical partitions)

and under (2) is (3)
Filesystem: linux-swap
Size: 5.06 GiB

Path: /dev/sda5
Status: Not active

---

### Post by aysiu on 2008-03-21
Okay, that's great. So delete /dev/sda1, /dev/sda2, and /dev/sda5. You can do this by right-clicking on each partition and selecting the Delete option. Then right-click on the newly created empty space, and select to create a new partition. Make that NTFS or FAT32.

---

### Post by wolfwood707 on 2008-03-21
Should I just delete the 5.06 GB partition and format it to NTFS?

Okey-dokey... here we go...

---

### Post by wolfwood707 on 2008-03-21
149.05 GB partition in NTFS... now let's see if the System disk works...

---

### Post by aysiu on 2008-03-21
> **wolfwood707 said:**
> 149.05 GB partition in NTFS... now let's see if the System disk works...
Good luck. Keep us posted.

---

### Post by wolfwood707 on 2008-03-21
By the way, now that I know how to do the partitioning stuff now (sorta), I'd like to reinstall Ubuntu on a partition at some point. I really liked it, I just HAVE to be able to use my wireless card and such.

Would it work well? Or would it be a big hassle?

---

### Post by aysiu on 2008-03-21
> **wolfwood707 said:**
> By the way, now that I know how to do the partitioning stuff now (sorta), I'd like to reinstall Ubuntu on a partition at some point. I really liked it, I just HAVE to be able to use my wireless card and such.

Would it work well? Or would it be a big hassle?
If you have at least 512 MB of RAM (I'd recommend 1 GB, though), try Ubuntu as a virtual machine within Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by wolfwood707 on 2008-03-21
uh-oh...

I did all the recovery stuff, rebooted, now...

"GRUB Loading stage1.5.

GRUB loading please wait...
Error 17"

And nothing more. o.O

---

### Post by aysiu on 2008-03-21
> **wolfwood707 said:**
> uh-oh...

I did all the recovery stuff, rebooted, now...

"GRUB Loading stage1.5.

GRUB loading please wait...
Error 17"

And nothing more. o.O
So Vista didn't overwrite the Master Boot Record?

It means the Grub boot loader is still on the MBR and trying to boot to Ubuntu but Ubuntu's not there.

Maybe this might help:
[Restoring Vista&#8217;s MBR/Bootloader](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

---

### Post by wolfwood707 on 2008-03-21
that did the trick!

Many thanks!

---

### Post by aysiu on 2008-03-21
> **wolfwood707 said:**
> that did the trick!

Many thanks!
Great. I'm glad that fixed it. And if you want to play around with Ubuntu without making a commitment to repartitioning, look into VirtualBox and the link I posted earlier.

---

