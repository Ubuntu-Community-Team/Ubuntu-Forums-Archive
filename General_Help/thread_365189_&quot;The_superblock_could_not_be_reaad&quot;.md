---
title: "&quot;The superblock could not be reaad&quot;"
date: 2007-02-19
forum: General Help
---

### Post by UbuntuUbuntu7 on 2007-02-19
A condensator in my powersupply exploded, and afterwards i could not start up my linux. It checks everytihing and it gets "ok", until it gets to "Checking all file systems" where it fails and i get the message "The superblock could not be read or does not describe a correct ext2 filesystem (and not swap or ufs or somethingelse), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:". I allso had a second drive with mp3 on. That disc is not found under my computer now. (Im running windows on a new disc). 

I would like to try to get the second disc with mp3 on to function. But the problem is that i can´t find it under "My computer", but it is found under "Control panel>System Properties>Hardware>Device Manager". I would like to start with trying to format the disc that i had linux on. But how can i do if i can´t get it to show up under "My Computer"? I tried "Testdisk" and it found the disc and i tried to erase the data or format it from there but it won´t show up anyway afterwards under "My computer". Any idea what i could try?

---

### Post by tgalati4 on 2007-02-19
Dear UU7

Sorry to hear of your disk troubles.  When a power supply goes, bad things can happen.

Rather than rely on Windows to recover your files, there are some Linux methods that have worked for me in the past.

First, how did you get Ubuntu installed in the first place?  You must have a live CD floating around that you can boot from.  (This assumes you have at least 256 MB of RAM or 128 MB of RAM and a valid swap partition.

If you are shy of RAM then try a copy of Damn Small Linux (damnsmalllinux.org).

Boot to a rescue shell--otherwise known as a root console.

Commands:

df -h               (to see what is mounted and how much space is available--note your device names:  /dev/hda1 /dev/hda2 /dev/hdb1 etc)

Let's say that the second partition of the first drive is toasty (assuming Windows is on the first partition of the first drive.)

sudo fsck /dev/hda2  (follow the prompts and answer yes to everything)

If the superblock is bad, there are usually a few good backups that can restore it.  If the head crashed into the platter (due to power failure) you may have several cuts in the platter that will show up as lost files.

If the superblock gets repaired then you should be able to reboot (removing the live CD). 

If you see endless errors and repairs during fsck then it may be time to trash the disk or use "Ultimate Boot Disk" and try reformatting the disk with a vendor specific diagnostic tool.

As far as your mp3 partition, you should be able to mount it using the Live CD and copy and paste data to a USB drive or network drive for safe keeping.

Tools such as cfdisk or parted can give you clues as to the partition damage, but don't make any changes unless you know what you are doing.

If the mp3 disk was originally a FAT32 drive, then a Norton Rescue disk can do a reasonable job of rebuilding the MBR's so that Windows can see it again.  If the drive was formated as ext2 for Linux, then Windows would not detect it at all.  The hardware would be registered, but the operating system wouldn't be able to read it.

One final approach, take the drives out and put them in another Linux machine can try fscking and mounting them.  That's what Linux clubs are for!

Best Luck,
Terry

---

