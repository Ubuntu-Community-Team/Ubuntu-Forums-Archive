---
title: "How to remove partitioned flash drive?"
date: 2015-09-14
forum: General Help
---

### Post by pderocco on 2015-09-14
I'm running a fresh installation of Ubuntu 14.04 LTS desktop.

I have a USB flash drive (a 1GB eSSD) with a partition table and two FAT16 partitions, one of which is a live image of a custom Linux version. The "dirty bit" which indicates possible file system corruption is always set in both partitions. If I run fsck.vfat -r on each partition, it tells me the dirty bit is set, and asks me if I want to clear it, to which I answer yes. If I run it again, it no longer says the dirty bit is set, so the fsck seems to work.

But if I unplug the drive and plug it back in, the dirty bits are back. So what do I do between fsck.vfat and unplugging it, to ensure that the fix is committed to the medium? I've tried the sync command. I've tried the eject command. I've tried umount-ing both partitions. I've tried umount-ing the whole device. I've tried right-clicking on one of the drive icons and selecting "Safely remove parent drive". Nothing seems to work. The dirty bits always come back.

This is the boot drive for an embedded Linux system. If I pull the drive from Ubuntu after the fsck, and stick it into the embedded system, the bootup warns about the dirty bits being set, so they are apparently set before yanking the drive, not after reinserting it into the Ubuntu system.

Can anyone explain what the relationships among sync, eject, umount and "Safely remove parent drive", and what steps I'm supposed to take before removing a USB flash drive?

---

### Post by The Cog on 2015-09-14
Try using -a instead of -r.
I found this on google: [https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by pderocco on 2015-09-14
The point is that fsck looks like it really is clearing the dirty bit, because if I run it a second time it doesn't complain. So that suggests that it is getting cleared in the disk cache, but that is never making it to the actual USB drive, so when I unplug it and reconnect it, the dirty bits are back. That's really what I'm asking about. How do people normally eject USB drives so that all writes are completed properly?

---

