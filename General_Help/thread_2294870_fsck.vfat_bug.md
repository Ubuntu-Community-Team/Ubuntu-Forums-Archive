---
title: "fsck.vfat bug"
date: 2015-09-14
forum: General Help
---

### Post by pderocco on 2015-09-14
I'm on a fresh installation of 14.04 LTS 64-bit desktop.

I have a USB flash drive (a 1GB eSSD, actually) with a partition table and two FAT16 partitions. The second is a bootable live image of a custom embedded Linux. When I run Ubuntu's fsck.vfat -a on it, it tells me that I have two bad short file names in the /EFI subdirectory called . and .. and it renames them, which of course ruins everything. Subdirectories are *supposed* to have . and .. entries in the FAT16 file system (and FAT12, and FAT32), except in the root directory.

Is there a more official place to report this bug?

---

### Post by SeijiSensei on 2015-09-14
You might have a problem contacting the developers: [http://daniel-baumann.ch/software/dosfstools/](http://daniel-baumann.ch/software/dosfstools/)

You can report it to Launchpad, but I'm not sure it will do much good there.  Your best hope might be with the [Debian maintainers]("https://packages.debian.org/squeeze/dosfstools").

---

