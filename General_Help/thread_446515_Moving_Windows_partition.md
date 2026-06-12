---
title: "Moving Windows partition"
date: 2007-05-17
forum: General Help
---

### Post by slumcat05 on 2007-05-17
I have a small partition with Windows 2000 installed for the infrequent occasions when I need to do something that is only supported in Windows (like flashing my DVD drive with a firmware update that could only be done in Windows, curse you Sony!...). Anyway, I found an old HD that works just fine, and I want to move the Windows partition to the new drive and reclaim the partition for use by Ubuntu. Is it possible to simply copy the partition to the new drive (both are NTFS, new drive has been wiped clean) using something like rsync, and then simply update grub to make the new drive bootable rather than the partition? Is there anything in the boot sector that won't get copied properly, or does grub handle all that?

The one major concern I have is that currently Windows is installed on what it calls the D: drive (in Ubuntu it's hda4, it skips the ext partitions before it, and my USB drive was powered on when I installed Windows, so for some reason it counts that as the first drive C:). The new drive is seen by Windows as G: (E: and F: are DVD and floppy). I feel like that might make it problematic, since all the settings, program files, etc. will be referencing D:, so is there a way to tell Windows to rename its drives, (i.e. change G: to D:), or fool it into thinking the new drive is D:, and will this mess with the way Linux views/names the drives? In fact, now that I think about it, I will be deleting the current hda4 partition and expanding hda3 (ext3) into the empty space, so Windows will then see the new drive as F:? You get the idea, it could get messy. Any advice?

If it's too much hassle/not possible, it's no big deal. There are very few programs installed (nearly all open source anyways, wooo!), but if it will be quicker than reinstalling Windows and those programs, that would be great.

---

### Post by slumcat05 on 2007-05-17
To clarify, I do have NTFS read/write supported installed and can currently read/write to the Windows partition (and the new, empty NTFS drive) in Ubuntu.

---

### Post by slumcat05 on 2007-05-17
Also, when I expand the existing linux drive into the space that used to be occupied by Windows, is it safe to do this with data on the linux partition, or should I back up this data just in case. If so, is there any good programs to backup/restore data? This partition happens to be my /home, so I am worried about messing up permissions and such, and do not want to simply copy and paste.

---

