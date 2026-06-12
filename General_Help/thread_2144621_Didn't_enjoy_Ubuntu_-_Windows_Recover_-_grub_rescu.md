---
title: "Didn't enjoy Ubuntu - Windows Recover - grub rescue"
date: 2013-05-12
forum: General Help
---

### Post by slimx on 2013-05-12
Edit: ORIGINAL ISSUE RESOLVED, but if anyone know the how to, please help me uninstall Ubuntu dual boot.

Hi,

 What I did in order: 

I installed Ubuntu 12.04 LTS today on my Windows 7 laptop to try it out. I installed it with the option to run windows simultanously.

I did not enjoy Ubuntu and wanted to get back to Windows.

I shut off the computer, turned it on again, and a bunch of options appeared from which I got to choose what to load up as the computer started up.

I picked regular Windows 7 I believe, and Ubuntu loaded again. 

I shut the computer off again and turned it back on, this time I chose the Windows 7 safe mode or recovery mode rather than the regular Windows 7 mode, and windows recovery loaded.

I hit that I wanted to recover my PC and it started formatting.

After the formatting, it reboot itself, only now, an error message is on my screen that says:

error: no such partition.
grub rescue>

I am not that savvy, but I assume I messed something up in regards to harddrive partitioning or something? I do not know. Please help me! How do I resolve this?

---

### Post by Mark Phelps on 2013-05-13
When you installed Ubuntu, did you use the SLIDER in the Ubuntu installer to shrink the Win7 disk space? If so, you likely corrupted Win7, rendering it unbootable.

You could try running Boot-Repair to see if that can get Win7 booting again:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by fantab on 2013-05-13
Have you uninstalled/removed Ubuntu completely? When you "recovered" Windows it erased Grub files from Ubuntu partition, so Grub is not booting. 
You have to fix MBR: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Boot-Repair too should fix it for you but I suggest you use your Windows 7 Repair to fix windows boot.

Good Luck...

---

### Post by slimx on 2013-05-23
Thanks for all the replies and sorry for taking this long to get back to you all.

I resolved it by inserting the Ubuntu CD I had created and reboot the computer (power switch) which let me reinstall Ubuntu alongside Windows and partition the harddrive again, this time, I did not touch the partition slider though. 

The first time I touched it, but put it like very close to the middle, and I do not understand why this matters anyway, maybe I was just unlucky the first time.

Anyway, Ubuntu installed, GRUB is back into place, and I am currently running both Windows 7 and Ubuntu at the same time.

Now I just need to figure out how I successfully can remove Ubuntu and Grub, along with "giving" the Ubuntu partition of the harddrive to Windows.

---

### Post by andrekp on 2013-05-23
So you installed Ubuntu, tried it for 15 minutes, and decided it wasn't like Windows 7 so you didn't feel comfortable and want to ban it from your hard drive?  This is a joke, right?

---

### Post by Mark Phelps on 2013-05-23
HOW did you do partitioning without using the Slider?  Did you do that in the Win7 Disk Management tool? Did you boot from a Linux CD/USB and use GParted to create the Linux filesystem partition?

How to remove it is critically tied to how you installed it.  So, we need to know more details about how it is installed.

To restore Win7 to the MBR, you need to go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You can then use that to restore Win7 to the MBR.

---

### Post by Maverick Meerkat on 2013-05-23
Well, now that they both work, why not leave things be for a while?
What didn' t you like about Ubuntu?
Maybe it is an easy thing to remedy.
Ubuntu doesn't install with all codecs and stuff that make life easy out of the box, but can be gotten easy enough.
Maybe some tweaks, like hiding the launcher?
You already did the hard part, give it a little more time.
It's only a suggestion, I'm okay either way :-)

Rick

---

### Post by slimx on 2013-05-30
> **Mark Phelps said:**
> HOW did you do partitioning without using the Slider?  Did you do that in the Win7 Disk Management tool? Did you boot from a Linux CD/USB and use GParted to create the Linux filesystem partition?

How to remove it is critically tied to how you installed it.  So, we need to know more details about how it is installed.

To restore Win7 to the MBR, you need to go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You can then use that to restore Win7 to the MBR.


No I did use the slider, I just didn't touch it from where it appeared. So in other words, it is partitioned where the Ubuntu installer suggested it to be partitioned.

A lot of what you are saying at the end sounds to technical to me :p I am already running Win 7 though, so it is working - what I need to do is get rid of GRUB, Ubuntu, and have the harddrive me "unpartitioned" into its regular state.

---

### Post by slimx on 2013-05-30
I did not like the "feel" of it - I wanted something more lightweight than Windows 7, which indeed Ubuntu is, but it didn't feel polished enough for me yet. It's the small details, like the clicks, the windows, etc.

> **Maverick Meerkat said:**
> Well, now that they both work, why not leave things be for a while?
What didn' t you like about Ubuntu?
Maybe it is an easy thing to remedy.
Ubuntu doesn't install with all codecs and stuff that make life easy out of the box, but can be gotten easy enough.
Maybe some tweaks, like hiding the launcher?
You already did the hard part, give it a little more time.
It's only a suggestion, I'm okay either way :-)

Rick

---

