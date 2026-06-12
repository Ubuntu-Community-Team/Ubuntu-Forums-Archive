---
title: "Uninstall Ubuntu?"
date: 2007-01-01
forum: General Help
---

### Post by uncommonjoe on 2007-01-01
I have recently installed Ubuntu and played with it for a month and decided all my windows programs don't work on there. I'm moving back to Windows 98 so how do I uninstall Ubuntu? I searched Google and found a website that said you have to put in a Windows 98 boot disk so I put that in and started her up and it still brought up Ubuntu. I messed with some stuff and now Ubuntu won't even load. It loads up the first thing OK but the next one (mounting something) doesn't go. I feel like I'm stuck in a hole that I dug my self in to. I looked for my Ubuntu CD to use that as a boot disc but I can't find it. 

**Question:** How do I uninstall Ubuntu / format my HDD?

Thanks!

---

### Post by Ramses de Norre on 2007-01-01
Just put something else on the ubuntu partition and boot into windows.. To uninstall grub you'll need to boot a windows install cd, go to the rescue prompt and type in these:
```
fixmbr
fixboot
exit
```

Too bad you didn't like ubuntu..

---

### Post by jonathan.lees on 2007-01-01
Well, if you must! You'll need to go into your computers's bios and tell it to boot from the cd. Usually to enter the bios you press the del key after the computer has been turned on, however on your computer it may be a different key such as esc or F2 or something.

In the bios you need to tell it to boot from the cd, where the location of this is depends on your bios. When your done, insert your windows 98 cd and reboot.

et voila! Now you can reinstall.

---

### Post by meng on 2007-01-01
It sounds as though your BIOS is not set to boot from the CD, as the previous poster mentioned. I'm not sure if Win98 will reformat and partition your drive (I suspect it will) but if you have problems you may need to use something like Partition Magic, or else the Ubuntu Live CD (hope you can find it again) which has a partitioning tool GParted.

I don't think that Windows98 will be receiving any further patches or security updates, so be very careful if this box is connected to the internet.

PS: It's not surprising that your Windows programs didn't work well with Linux, what is surprising is that you expected they would. Good luck anyway.

---

### Post by uncommonjoe on 2007-01-01
I did try setting the BIOS to boot from the CD. I also have a floppy boot disk and have tried to boot from that as well but none of them work. I know the CD-ROM drive works as well as the CD it's self.

I honestly don't like Windows 98. My machine is old and can't handle XP (besides it costs $100). I really liked Ubuntu but it can't run my programs or games (Yeah a few of them are M$ games).

Thanks so far guys.

---

### Post by meng on 2007-01-01
If your computer isn't booting from the Win98 disk, then something is wrong with the BIOS/settings, the CD-ROM drive or the CD-ROM itself. The presence of an OS on the hard drive should not be relevant UNLESS there is a problem with one of the other three.

---

### Post by moshuptrail on 2007-01-01
Going BACK to Win98??

I loved Win98, but now that MS has de-supported it, if you re-install you will not be able to apply all the dozens of security patches.  This will leave your w98 pretty vulnerable to many attacks.

There are a lot of Windows programs, especially games that don't run on Linux.  Some you can get to run in Wine or VMware, but what's the point?  Just dual boot, or stick with Windows.

---

### Post by uncommonjoe on 2007-01-01
I know both CD-ROM drives work fine. I have used them before.

This is exactly what I did:

Turn on PC and it brings up memory test and such then brings up four options:
Setup (DEL), Boot Menu ( F8 ), Network Boot (F12), Skip Menu Test (ESC). I hit F8 and brings up a five options:

Floppy                 :    1st floppy
IDE-0                  :    IBM-DPTA - 371360
CDROM               :    CD-ROM Drive - F5E
ATAPI Zip C        :    RLGXVOR CD/R" "PZ - W1212A
Network

I chose the CDROM option then it says GRUB Loading... and says press ESC to enter menu. I let it load the GRUB and it brings up the Ubuntu window and it tries to load but doesn't work. So I restart my computer and do the whole set again except I press ESC when it loads the GRUB and it brings up 3 more options:
Ubuntu, Kernel 2.2.15-23-386
Ubuntu, Kernel 2.6.15-23-386 (recovery model)
Ubuntu, memtest 86+

It says below that
"Use up and down arrows to select 
Press enter to boot the select OS, 'e' to edit commands before booting or 'c' for command line."

I chose 'c' and try fixmbr, fixboot, exit but all I get is Error 27: Unrecognized command.

---

### Post by meng on 2007-01-01
I wonder if when you get the boot menu you are able to change the ORDER of the five options. Perhaps it's not selecting a single option but showing you an order of priority, in which case the hard drive appears higher on the order than the CD-ROM drive.

---

### Post by uncommonjoe on 2007-01-01
I did change the order or the boot options to CD-ROM first then Floppy 2nd and nothing on the 3rd. I still haven't got it to boot up. I had a friend helping me but he couldn't get it fixed.

My BIOS is American Megatrends if you needed to know.

---

### Post by meng on 2007-01-01
Well, if your BIOS is set correctly and the CD-ROM and drive are fine, then there's no reason it should be going to GRUB! It's a real puzzle.

---

### Post by Keldek on 2007-01-01
It's quite possible, especially being that Win98 is very old, that your win98 cd & floppy are unusable?

What I mean by that is over time, especially the years you've had to own the win98 disks, maybe they've gotten too scratched up or the data has somehow been corrupted and the floppy/cdrom drive can't read the disks?

And to be quite honest, if you're having trouble getting programs to run in linux, chances are you'll have just as much trouble getting newer software to run in windows 98.

---

### Post by lyceum on 2007-01-01
It has been years, but I use to re-load Win98 every 6 months, and I always had to fdisk first and wipe everything, restart, go back to fdisk and re-format the hard drive, because 98 did not do that for you. I wish I could tell you more, I know I had to type is a word that started with an 'S" Startup? Setup? I'm sorry, I hope this helps get you on the right track. It's just been too long...

---

### Post by uncommonjoe on 2007-01-19
Thanks guys! Today I decided to format that HDD again and actually got it to boot from a new floppy boot disk! I have it in DOS now and I forgot the command to format. What is it? I've tried format: C (in A: ), format C: (in D: ) but none of those have worked.

Thanks!

---

### Post by lyceum on 2007-01-19
> **uncommonjoe said:**
> Thanks guys! Today I decided to format that HDD again and actually got it to boot from a new floppy boot disk! I have it in DOS now and I forgot the command to format. What is it? I've tried format: C (in A: ), format C: (in D: ) but none of those have worked.

Thanks!

To format, after restart just go back to fdisk and create a new partition. If I remember correctly, restart, once in dos, pick the right drive (D:// "enter" or what ever drive Windows is in) and type "setup or start up, I think t is the later.

If you want to try Ubuntu again, there is a project working on loading Ubuntu on Windows without messing up Windows.

[http://www.ubuntuforums.org/showthread.php?t=338279](http://www.ubuntuforums.org/showthread.php?t=338279)

---

