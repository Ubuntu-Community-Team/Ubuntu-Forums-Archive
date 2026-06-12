---
title: "Grub Won't Load on Dual-Boot Except When Live Disc is in Drive"
date: 2007-06-15
forum: General Help
---

### Post by kables on 2007-06-15
Firstly, this is my first post ever, which is hard to believe considering how much valuable information I've found in these forums. So, thanks.

Secondly, I've been running a dual-boot Ubuntu/XP system for about three months ago, and am currently running Feisty (upgraded from Edgy). 

Two days ago GRUB failed to load, and hasn't loaded since. Now all it does whenever I power up is flash a bit across the top of my screen, and then a box containing a down-pointing arrow and a flashing cursor appear at the bottom. (The rest is black screen.) Grub never appears; I can't boot into any OS.

I discovered that when I first boot from the live CD, and then tell the system to "boot from first hard disk," that GRUB loads, and I can boot fine. But it's a pain to do this every time.

I can't recall that I did anything to the system other than the usual system updates. Any thoughts? I've scoured the forums, but haven't come up with anything.

---

### Post by 67GTA on 2007-06-15
Try to restore grub. 
[http://ubuntuforums.org/showthread.php?t=387856](http://ubuntuforums.org/showthread.php?t=387856)

---

### Post by kables on 2007-06-15
I tried restoring GRUB, which led me to the discovery about the live disc. No dice, though. Still black screen.

---

### Post by Nzer24 on 2007-09-06
I have an almost identical problem.

I tried to repartition my hard drive and install ubuntu and fedora (and xp) on a triple boot.
After both were installed, it said "no bootable device" on startup.
I used xp install cd to clear the mbr, then reinstalled grub.
Now I can boot through the live cd, but not without it... and the "no bootable device" still comes up normally.

I have the Intel DP35DPM Desktop board (DP35 chipset)

Therefore, it shouldn't fix it to clear the mbr, so you probably shouldn't waste your time doing that... plus it can destroy your partition map.

---

### Post by Nzer24 on 2007-09-06
I just fixed my problem, so try this:

Download SuperGRUB and write it to a cd
reinstall GRUB:

type:
find /boot/grub/stage1
root ( )      (put in the output of the find command instead of the space)
setup (hd0)

Now eject the supergrub cd and on you next boot, grub will start.

Hope this works for you!:)

---

### Post by merlinus on 2007-09-06
You can also do this in a terminal via the ubuntu live cd.

-merlin

---

