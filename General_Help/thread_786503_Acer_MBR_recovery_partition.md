---
title: "Acer MBR recovery partition"
date: 2008-05-08
forum: General Help
---

### Post by carbonhorse on 2008-05-08
Ok I have been trying to solve this problem by searching forums, for over a week, with no joy. I have an almost new Acer laptop 5315 series, (the cheap one). Vista got a virus, Trojan, AIDS or something, and was real sick. Just getting slower and slower. So I downloaded the latest Ubuntu 8.04 and installed. About that time Vista went Asta completely and will not boot up at all. No biggy, I did not touch the recovery partition, and only resized C: Vista bigger, to give it more room to breath. Only problem is that now the Acer d2d system recovery does not work at startup Alt+F10. Some research reveals that the linux bootloader "Grub" has overwritten the acer MBR. More research brings a bootload of options, all of which either don't work, or are so lacking in detail they make swiss cheese seem complete. Apparently I can boot staight into d2d with a linux live CD, please explain. Opperating systems need precise instructions, so do I. I have Madriva, Knoppix, Big Daddy, Navidia, Gparted. I even read on a post that I can restore the MBR by typing mbrwrdos/recovery at DOS. Now I havn't been able to reach DOS since windows 98. Can someone please provide me with some detailed, step by step assistance. :confused:

---

### Post by Zorael on 2008-05-08
I managed to do the same thing, but I can boot it fine via grub.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Acer Recovery Partition
root            (hd0,0)
savedefault
chainloader     +1
```
One of the first things I did when I got my laptop was to make a backup of that partition, but sadly I wasn't knowledgeable enough to know I should've backed the MBR up as well.

There *is* a file called mbr.bin in the root of that partition, at least on mine, as well as one called rtmbr.bin. I've tried to restore these with windows applications, but then the system wouldn't boot, so I had to restore grub with a live cd. If you use testdisk and install a standard mbr it'll boot the partition marked active (like the standard Windows mbr), but the ALT+F10 override doesn't work.

---

### Post by carbonhorse on 2008-05-09
Thanks Zorael. Every little bit of information helps. The so called technitions at Acer say that I need to reimage the drive, which of corse I don't. But if those responsible for my dilema will offer no assistance, then I will have to bite the bullet and fork out for this option. Then tell everyone I encounter to avoid linux like the plague, which it is, just another useless virus.

---

### Post by ugm6hr on 2008-05-09
Some points:

1. How did you resize the Vista partion?  If you used Ubuntu, that may have been the problem.  GParted cannot safely resize Vista partitions.

2. GRUB should be able to access the recovery partition - it does on my Acer 5051 laptop.  Post the contents of /boot/grub/menu.lst and the output from:
```
sudo fdisk -l
```

3. Linux is not a virus.
> But if those responsible for my dilema will offer no assistance...
Perhaps you should have read some more before installing, or asked for help first.  The person responsible is probably you.

---

### Post by carbonhorse on 2008-05-10
Sorry ugm6hr since I cannot get the wireless working in ubuntu, I have no internet connection on my computer and cannot post the contents of my boot/grub/menu. It's all gibberish to me anyway. Yes I have read that I can boot into recovery from linux. My problem is that I have not read any details on how I might do this. And linux may not be a virus, for all I know, a properly updated linux os may suit my perposes better than windows. It just seems to me that the people posting on these forums view it as more toy than tool, and I need a functional tool right now. Anyway I got your attention. Kudos on leaving the thread up.
I do not recall reading any warning, either in the publications promoting experimentation with linux, or on the any linux site, that this would interfere with recovery options. You are correct though, I should have burnt a recovery CD on purchase of the unit. My bad.:(

---

### Post by ugm6hr on 2008-05-10
Linux is not a toy either.  The reason most posts here may suggest that is that the people who use it as a main OS for work don't need / want help here.  Those of us who frequent the forum and use it as a "functional tool" try to help other users make the transition.

If you didn't read that installing Ubuntu (or any OS) with repartitioning of a HD could affect data integrity, you didn't read enough.

Anyway - getting to your actual problem...  Please actually provide some information for people to help.

How are you connecting to the internet now?

How did you install Ubuntu (exact details of what you did - e.g. booted from Live CD, partitioning details, installation from within Windows etc)?

If you can't get online from Ubuntu, use a USB flash disk to copy and paste details to this forum (Text Editor will do it).  Follow the link about Code / Terminal in my signature for details on how to use Terminal.  To open the relevant file, use:
```
gedit /boot/grub/menu.lst
```

It should have an entry near the bottom like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Out of interest, do you have wired ethernet?  And do you want to actually use Ubuntu at all, or just reinstate Vista?

---

### Post by Zorael on 2008-05-10
Not to be an (donkey), but yes, this is user error. With knowledge of how boot sectors and MBRs work, I could've avoided this - but I plunged into it and, well, here I am.

There's some interesting reading over here: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm).

I'd like to see Acer be more assisting in these matters, too, but the support crew is likely just not allowed. That said, if the partition is still there then there's no reason grub shouldn't be able to load it. After all, what the Alt+F10 override did was just to load the non-active partition instead of the active one (installed XP).

---

### Post by carbonhorse on 2008-05-12
Sorry to be gone for so long. As you may have guessed I have no net access of my own. I have decided to concentrate on my wireless problem in Ubuntu and get back to this one at a later date. Just a link that I thought might be of use to Zorael. 

[http://www.roundtripsolutions.com/blog/2007/10/18/300/acer-disk-to-disk-d2d-recovery-broken/](http://www.roundtripsolutions.com/blog/2007/10/18/300/acer-disk-to-disk-d2d-recovery-broken/)

---

