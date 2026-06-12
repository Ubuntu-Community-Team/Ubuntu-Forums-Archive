---
title: "After Installing xp-Can't access Grub or Vista bootloaders"
date: 2007-06-24
forum: General Help
---

### Post by NNG on 2007-06-24
Ok, well I installed Xp proffessional to my computer with Vista ultimate 64 bit and Ubuntu Linux installed. Now whenever I boot the system it directly loads xp without giving any option to do anything else.

As a more detailed summary of my situation, I built a computer a few days ago and originally installed  Vista Ultimate 64, Ubuntu Linux 32, and Vista Ultimate 32 in that order. I did Vista ultimate 32 bit because I needed some version of 32 windows to use my ipod and I couldn't install windows Xp without a floppy drive (which I didn't know before hand) I installed Vista 32 and 64 to one 500 GB hard drive and Ubuntu +its swap partition to the other 500 Gb hard drive. Today I got my floppy drive so I installed Xp replacing my 32 bit ultimate OS. However, after I installed Xp, it completely bypasses both the grub and Vista bootloaders so I can't load either Vista or Ubuntu.

Before it was set up so that Grub gave me the option to load Ubuntu or the Vista bootloader then I would choose between windows versions from there. Probably not the best set up but I'm still relativity new to all this.

I did check to see that the partitions for Vista and Ubuntu are still there and they are but other than that, I'm really lost on what to do and I really need some help.

---

### Post by Azakus on 2007-06-24
XP rewrote your mbr. You're going to have to get a LiveCD and reinstall grub on your MBR. Here's a guid to doing that.
[ How to install Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by NNG on 2007-06-24
> **Azakus said:**
> XP rewrote your mbr. You're going to have to get a LiveCD and reinstall grub on your MBR. Here's a guid to doing that.
[ How to install Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")
Ok, I just did that and it brought back Grub alright. However, now I cannot access either windows OS's because in grub, when I click to load the Windows Vista/longhorn loader I get error ```
12: Invalid device requested
```
Making progress though :P

Edit: I'm going to see if Vista repair Cd can fix the vista bootloader on its own and see if that works.

Edit 2: Ok after trying that something really weird happened. The Vista Cd couldnt see the actual Vista OS but it could see all of the partitions of windows. Well that was useless :(

---

### Post by bigken on 2007-06-24
[this]("http://ubuntuforums.org/showthread.php?t=398122&highlight=ad+vista+to+grub") might help

---

### Post by NNG on 2007-06-24
> **bigken said:**
> [this]("http://ubuntuforums.org/showthread.php?t=398122&highlight=ad+vista+to+grub") might help
I don't think that will help because how his problem and my problem arose are quite different. The poster used Linux to repartition a Vista partition and what caused my problem was using windows to **create** (didnt do anything to any other partitions) a partition and install it.

---

### Post by Azakus on 2007-06-24
You need to add 
```
savedefault
makeactive
chainloader     +1
```
to the end of grub's XP and vista sections in /boot/grub/menu.lst in order to make Grub use Vista's and XP's bootloaders.
{EDIT} You have all OS's on the same harddrive right? If not, you need to do even more to make Vista and XP boot.{/EDIT}

---

