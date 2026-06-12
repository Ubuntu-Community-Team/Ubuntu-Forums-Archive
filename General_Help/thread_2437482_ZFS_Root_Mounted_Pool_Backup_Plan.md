---
title: "ZFS Root Mounted Pool Backup Plan"
date: 2020-02-24
forum: General Help
---

### Post by ltburch2000 on 2020-02-24
So now that Ubuntu 19.10 can natively install to ZFS and this is planned to be expanded in 20.04 LTS.  How can we online backup our ZFS pools and restore successfully?

I had been using LVM with ext4 and taking snapshots and backing up with fsarchiver but had no luck restoring to a correctly booting system, somehow the boot loading would always get messed up.

Any good plans/tools out there for backup and recovery with ZFS pools?  I suppose a zfs snapshot with a send to a network drive, but will that catch all the needed boot stuff?  How do I square away the boot stuff if I need to recover from a failed drive?

Lee Burch

---

### Post by kevdog on 2020-02-24
I'm currently using znapsend as part of my backup strategy for ZFS.  And yes that will cover every zfs partition except boot.  I honestly don't have a good backup strategy for /boot since that's running for me at least on a vfat32 partition.  I could recreate the partition if I had to with chroot (assuming all the other partitions had been restored successfully), however I'll probably just use either borg or rsync to backup this partition.  I'm not sure if its as crucial to backup this partition as often since once booted I could update the kernel and regenerate the initramfs after the update.

---

