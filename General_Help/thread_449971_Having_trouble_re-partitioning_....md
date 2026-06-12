---
title: "Having trouble re-partitioning ..."
date: 2007-05-20
forum: General Help
---

### Post by Mr-Z on 2007-05-20
Hello!  I installed Ubuntu 6.0.6 on my windows XP machine and successfully got it dual-booting.  Everything is fine except that I forgot to make a Fat32 partition so that I can trade files between XP and Ubuntu.
I re-booted using the live install CD, and used 'sudo gparted' to get to the partition program.  From there I reduced the size of my ext3 partition by 1.5Gb and selected the Fat32 format.  It ran for a moment and gave me an error saying that the device was busy and could confuse the system, and that the kernel should be restarted.  I re-booted into the live install again and this time went into drives and disabled hda1 before re-attempting, but it still gave me the same error.  So I downloaded the GParted live CD iso and booted with that.  Once it booted and loaded the devices it showed that the 1.5Gb partition was there, but had no format.  I clicked "New" and selected Fat32 again, it did it in 2 seconds with no errors or anything, shut down and rebooted normally.

Now Ubuntu is seeing 'Partition 4' at 1.45 Gb and seems to recognize it as a Windows format, but it says that the drive is inaccessible, and the size meter says "free space not available".  Any suggestions?  I suppose I'll go back into GParted live and erase/re-create the partition and see if that works.  Any help I can get is greatly appreciated, I've tinkered with Linux a little here and there but this is my first time putting it on my own PC.

For the record I'm running a Toshiba Satellite w/ 1.3Ghz Celeron and 768Mg RAM.  I've got 26.5Gb on the NTFS partition, 9Gb on the ext3, 512Mb swap and 1.5Gb on the Fat32 partition in question.

Thanks!

---

### Post by Mr-Z on 2007-05-20
Well, the answer was more obvious than what I was looking for ... just needed to mount the partition :oops:  I had assumed that's what the 'enable' function in the 'disk' tool was doing so I didn't bother to try it earlier.

Problem now is that I can't seem to USE the partition :???:

It wouldn't let me write to the partition because the directory is owned by 'root'.  I changed the owner to my username, but it changes back to root when I mount the partition there.  I can't seem to chmod it either ... from what I can tell this should work:

sudo chmod a=rwx /mnt/hda4

But no variation of chmod is giving me write access.  I also tried changing my username's group to "root" but that didn't work either.  I have to use the sudo to add anything to the drive (although it does work like that, so I know the partition is accessible for writing).  This whole "You're not allowed to be root on your own machine" thing is kind of starting to bother me.

What's the command line for the file browser?  I'm assuming that if I run that with sudo from the command line it should let me write to the folder ... but I'm setting this up mainly so that I can share my Firefox/Thunderbird profiles between Ubuntu and XP, so really I need to be able to write to that partition from my current user and not only root.

Any help is greatly appreciated!!

---

### Post by Mr-Z on 2007-05-21
Forgive me, I'm new here.  Is it too early to bump?

It figures, I found the answer *immediately* after I bumped.  Got it all figured out now, for real this time :D

---

