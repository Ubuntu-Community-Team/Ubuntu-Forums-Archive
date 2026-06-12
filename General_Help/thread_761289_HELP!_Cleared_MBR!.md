---
title: "HELP! Cleared MBR!"
date: 2008-04-21
forum: General Help
---

### Post by shavenlunatic on 2008-04-21
I need some help.

I won't bore you with the story of how I got to this point.  But I had an issue with a 2nd sata hdd on the pc, i booted with UltimateBootCD and ran fdisk on the 2nd drive, cleared out the partitions, ran fdisk /mbr (i have no idea why I thought it would do this to the 2nd drive, it was about 2am and I wasn't thinking)

So now the 1st drive just boots straight into windows and grub doesn't even get a look in.

To sum it up, i need to get grub back on the 1st drive so I can boot into Kubuntu :(  (losing the data isn't an option... hopefully)

Thanks in advance

---

### Post by dcstar on 2008-04-21
> **shavenlunatic said:**
> I need some help.

I won't bore you with the story of how I got to this point.  But I had an issue with a 2nd sata hdd on the pc, i booted with UltimateBootCD and ran fdisk on the 2nd drive, cleared out the partitions, ran fdisk /mbr (i have no idea why I thought it would do this to the 2nd drive, it was about 2am and I wasn't thinking)

So now the 1st drive just boots straight into windows and grub doesn't even get a look in.

To sum it up, i need to get grub back on the 1st drive so I can boot into Kubuntu :(  (losing the data isn't an option... hopefully)

Thanks in advance

Just do a forum search for "restore grub" and follow the instructions.

---

### Post by kellemes on 2008-04-21
You can download/burn/boot from [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and let it boot any bootable partition on your system, or even restore your bootloader.

---

### Post by housam on 2008-04-21
recover grub using this guide : [[COLOR="Red"]_restore grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by shavenlunatic on 2008-04-21
> **housam said:**
> recover grub using this guide : [[COLOR="Red"]_restore grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

thanks to all for advice.. and thanks for link housam.

Apologies for not managing to find it myself.. have been in a bit of a panic and am suffering from a lack of sleep :)

---

### Post by shavenlunatic on 2008-04-22
in the end it wouldn't mount the partition, no matter what method I tried, just kept getting hammered with error messages so I ended up having to boot from liveCD, running nautilus as root and backing up anything I could to the external drive.

Thanks for help though

---

### Post by DBrocks on 2008-04-22
Well then, could you please mark this thread as solved? it makes the lives of people trying to find a solution, and the helpers easier.

Thanks!

---

### Post by shavenlunatic on 2008-05-05
i really would, if I could find out how to

or do we just mean change the title to include [SOLVED]?  I'll do that :D

---

