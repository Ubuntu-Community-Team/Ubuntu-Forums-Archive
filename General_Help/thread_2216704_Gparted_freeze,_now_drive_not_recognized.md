---
title: "Gparted freeze, now drive not recognized?"
date: 2014-04-13
forum: General Help
---

### Post by RallyDarkstrike on 2014-04-13
Hi all,

I've got an old 20gb IDE drive that I want to put into an older machine to install Linux on, but first I need to use it to back up some files from the current Windows install to transfer to another Windows machine for safe keeping. So, what I was going to do is copy the files off (which went fine), format the drive to NTFS (it was FAT32) and then back the files up and eventually install Linux on the same drive.

I hooked it up to my USB HDD adapter and plugged it into my computer and booted to a Xubuntu 13.10 Live cd. From there, I ran sudo Gparted and proceeded to erase the existing FAT32 partition and re-add the new NTFS partition on the whole drive. While Gparted was adding the partition, Gparted froze....I let it set for awhile and nothing happened, so I Force Quit it.

Now NOTHING will recognize the hard drive. I haven't installed it directly in a computer yet, but I've tried on 2 different PCs in 2 different Linux Live distros with the USB adapter and nothing will get the drive to recognize again in GParted...? It isn't even listed there as having no partition table or anything?

I can hear the drive spool up so I know it is still working, just curious if anybody had any ideas before I try directly installing it in a machine?

Cheers and thanks!

---

### Post by gedakc on 2014-04-13
From your description it sounds like the drive might be failing.  To check, scan through the output of the **dmesg** command to see if there are any problems reported with the drive (e.g., /dev/sdb).

---

### Post by RallyDarkstrike on 2014-04-13
Pretty sure the drive is fine as I use it often with no problems. it seems to just take a long time for Linux to "first read" it before I can do anything to it. Both the machines I tested it on with the USB adapter eventually detected it, I just had to let them wait for a minute or more. After that it was fine! So, false alarm I guess....guess I was just used to them being much more quickly detected on my other hardware!

---

### Post by rbmorse on 2014-04-15
It may look like it's working, but I'd follow gedakc's advice to check dmesg output and make sure there are no drive-related errors reported.

---

