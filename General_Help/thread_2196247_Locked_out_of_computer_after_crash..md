---
title: "Locked out of computer after crash."
date: 2013-12-28
forum: General Help
---

### Post by myrtle001 on 2013-12-28
Hello all,

I'm no longer able to boot into any operating system on my computer. Not knowing what details are important and which ones are not at this point, I'll be as thorough in my explanation as I can be:

About an hour ago, I was watching a video on YouTube (using Chromium on Ubuntu 13.10), and I decided to plug in my headphones. I plugged them in, went to the Sounds program to switch audio output from "HDMI" to "Headphones", and then a few moments later Chromium went dark (the animation that Ubuntu shows when a program stops responding). The video continued to play, and I was strangely still able to pause/play it. The close/minimize/maximize buttons on Chromium didn't work. I right clicked on Chromium in Unity and clicked quit to close it since it wasn't responding. After a few moments, Chromium finally closed, and then Unity crashed. All that was visible on my screen was the Sounds menu (minus the title bar from Unity) and the background. The Sounds menu was not responding to mouse clicks. I waited for a few minutes to see if Unity would restart, but I got impatient after about a minute. I then held in the power button for 10 seconds to do a hard reset.

When my computer restarted, I was brought to the "Loading Operating System..." screen my motherboard typically puts up, but then it said something along the lines of "error: no such device" and brought up a "grub rescue" prompt. Usually, GRUB would pop up and allow me to select from Ubuntu, a few recovery options for Ubuntu (if I'm remembering correctly), and an option for Windows 7 (dual-booted).

My computer is set up with some complexity (and I can't quite remember how it's set up). I built my computer from parts on Newegg (I'll list the parts at the end of this post in case they matter). I have three storage drives on my computer: a 1TB HDD, a 60GB SSD, and a 128GB SSD. I know the entire 60GB SSD is dedicated to Windows. If I'm not mistaken, the 1TB is evenly split between Windows (as a drive for my to store files to) and Ubuntu (as the /home directory and most of the other directories I think). The 128GB SSD I believe I have set for Ubuntu's /boot directory and a few others, and I believe it has the 16GB SWAP partition on it as well (unless that was on the 1TB HDD). My apologies for not remembering which directories are on which partitions.

If it's at all important, I frequently run into identical crashing issues while playing games in both Ubuntu and Windows. I'll play a game, and then at a random time the computer will crash to a black screen and then after about a half a second to a colored screen, typically white/grey/cyan/magenta/yellow. I tried to determine the cause of that problem at some point and gave up.

Also, if it's important, I believe I remember running into a similiar GRUB problem when I installed my 128GB SSD (I bought that a few months after building my computer). I've never really had any GRUB problems since then (meaning it's been running fine for over a year now).

I'm currently writing this on FireFox using an old Ubuntu 10.10 LiveCD that I have.

What should I be doing? What went wrong? Any help is appreciated!

Thanks in advance!

myrtle001

--
CPU: AMD FX-8150
Cooling: Cooler Master Hyper 212 Plus
Motherboard: Gigabyte GA-990FXA-UD5
PSU: Rosewill HIVE 750W
Video Card: EVGA GeForce GTX 560 Ti 448 Cores FTW
Memory: Corsair Vengeance 16GB (2 x 8GB) DDR3 1600
Storage #1: Seagate Barracuda 1TB 3.5" SATA 6.0Gb/s
Storage #2: Corsair Force Series 3 60GB 2.5" SSD
Storage #3: Samsung 830 Series 128GB 2.5" SSD
OS: Ubuntu 13.10 64-bit, Windows 7 Home Premium 64-bit

---

### Post by myrtle001 on 2013-12-28
Additionally, it might be worth noting that the 128GB SSD doesn't contain a valid partition table according to fdisk.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

[B]Disk /dev/sda doesn't contain a valid partition table
[/B]
Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a7b2dad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        7297    58509312    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7dc9e5e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488379392    7  HPFS/NTFS
/dev/sdc2           60801       63233    19530752   82  Linux swap / Solaris
/dev/sdc3           63233       75390    97656250   83  Linux
/dev/sdc4           75390      121602   371194336   83  Linux

```

---

### Post by steeldriver on 2013-12-28
Well you could try boot-repair ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ) however given the history of crashing I'd suspect the primary SSD (which likely had the grub bootloader on it) was failing and is now toast

---

### Post by oldfred on 2013-12-28
Best to never do hard shutdowns as that often corrupts file system if something is in the middle of doing anything.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

I have generally suggest you have a repairCD or Flash drive for the current version of every operating system you have installed. And with multiple drives have a operating sytem on every drive, with its boot loader on the same drive. So when (not if) one drive fails you can boot another or a repairCD/flash drive.

---

### Post by myrtle001 on 2013-12-29
I managed to get Windows 7 to boot up for me. I launched the Windows 7 installation disk and restored the MBR in the command prompt. So, now Windows seems to be working just fine. I'll probably end up reinstalling Linux, which I think I'm just fine with.

I haven't confirmed yet if the 128GB SSD is dead yet, but it is the only drive that is offline by default in Window's partition manager (it said something about it needing to be initiated and gave me a few options, but I decided not to tackle that at the time).

I forgot to mention that my home folder was encrypted. Recovering those files turned out to be the hardest part of the process.

> **oldfred said:**
> Best to never do hard shutdowns as that often corrupts file system if something is in the middle of doing anything.

Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

I'll keep that in mind, oldfred. **R**eboot **e**ven **i**f **s**ystem **u**tterly **b**roken...;)

Thanks for the help!

myrtle001

---

### Post by kurja on 2013-12-29
another way to sanely recover/reboot if your gui crashes, is via terminal - ctrl+alt+F1, login and 'sudo shutdown -R now' to reboot or try and restart your gui with 'unity & disown' (then ctr+alt+F7 to return to gui).

---

### Post by oldfred on 2013-12-29
Windows will always tell you that you need to format Linux formatted partitions. So it is not telling you if you have issues or not. It does not see the Linux partitions. 

Does UEFI/BIOS show drive and from Ubuntu Disks or Disk Utility what is Smart Status? It is Disk Utility in 12.04 and Disks in 13.10, not sure exactly when it changed.

---

