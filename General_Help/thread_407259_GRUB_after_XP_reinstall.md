---
title: "GRUB after XP reinstall"
date: 2007-04-11
forum: General Help
---

### Post by Shampyon on 2007-04-11
I decided to go for a clean reinstall of XP to get rid of all the junk accumulated ofer the years, while keeping Ubuntu as my primary OS. I checked a bunch of other threads for the most important step in the process: recovering GRUB.

I backed up menu.lst using:
```
$sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp070412
```

After reinstalling XP I used the xUbuntu Live CD to open a terminal (as my Ubuntu LCD doesn't seem to want to go to Terminal after the expected difficulties with my ATI video card). I used the following to reinstate GRUB:

```
$sudo grub
$find /boot/grub/stage1
$root (hd0,6)
$setup (hd0,6)
$quit
```

Upon reboot, the Windows MBR is still in control. I go into xUbutnu Terminal again, this time attempting to restore GRUB simly by reversing the initial backup command:
```
$sudo cp /boot/grub/menu.lst.bkp070412 /boot/grub/menu.lst
```

No luck. I even tried using both xUbuntu and my old Ubuntu 5.10 discs to do the following:

> Boot CD>>Install
Disk Partitions>>Manually Partition
Mount the partitions:
```
/
/boot
swap
```
Do not format partitions, ignore errors. Continue until back to install menu, go to: Install GRUB


The output I got from that indicated it was successful, so I rebooted. No such luck; Windows MBR is still in control. I'm stuck using a fresh install of XP, with none of my apps or bookmarks or files.

Where do I go from here?

---

### Post by confused57 on 2007-04-11
Setup (hd0) would install grub to your mbr, overwriting Window's IPL code:

```
$sudo grub
$find /boot/grub/stage1
$root (hd0,6)
$setup (hd0)
$quit
```

---

### Post by Shampyon on 2007-04-12
Getitng closer. GRUB starts up and all the options I used to have are there, but I'm getting a major problem:

> Error 17: Cannot mount selected partition

I can still boot into XP, just not my Ubuntu partitions. Tried
$sudo nano /boot/grub/menu.lst
but it comes up as "File not found"... So strange.

---

### Post by confused57 on 2007-04-12
> **Shampyon said:**
> Getitng closer. GRUB starts up and all the options I used to have are there, but I'm getting a major problem:



I can still boot into XP, just not my Ubuntu partitions. Tried
$sudo nano /boot/grub/menu.lst
but it comes up as "File not found"... So strange.

You can try using the live cd to mount your linux partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Since you're getting a grub menu at boot, you might try using the grub Command Line Interface to investigate your computer:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Another thing you might want to do is download a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Shampyon on 2007-04-12
Just tried out Super GRUB Disk. No luck, all attempts failed.
I'll try out the other two suggestions now.

EDIT:
Used the LiveCD suggestion. Managed to mount my Home partition in the live session. Opened my backup file *menu.lst.bkp070412*, copy-and-pasted the contents into *menu.lst*. Rebooted. No effect.

Damn, this is frustrating.

---

### Post by Shampyon on 2007-04-12
Retried the GRUB menu command line fixes during boot time instead of LiveCD session.
Still no change. Worse yet, something's happened to screw up the LiveCD sessions. In order to start the sessions before, i had to wait for it to fail to load xserver (due to my ATI card), then do *sudo dpkg-reconfigure xserver-xorg* to change to the* vesa* driver to start the live session. No it all just hangs before the command prompt can appear.

I'm considering just wiping XP completely from my hdd. I only really kept it for one or two apps (which I don't often use) and for gaming (which I dont often do). Maybe install xUbuntu to the WinXP partition, then reconfigure GRUB to load my Ubuntu partition as primary, then wipe xUbuntu and use that partition as storage space.

---

### Post by confused57 on 2007-04-12
You could boot up the live cd, then post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

then mount your Ubuntu root partition and post your menu.lst:
```
cat /boot/grub/menu.lst
```

You might want to run a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by Shampyon on 2007-04-12
I didn't get to see your last reply because I ended up losing internet access due to some of the other methods I tried. In the end i simply installed Ubuntu on the old XP partition (number 1 of 4), reinstalled my apps and copy-pasted all their configuration files over from the old Ubntu partition (which was number 4 of 4). Now my system is back to the way it was, minus XP.

Since I don't really use it often any more, I'm just gonna let it go. It was really only for gaming and the occasional use of Photoshop, so if I really wanted I could just save some cash and create a dedicated gaming box.

Thank you for your help. It's very much appreciated (^_^)

---

