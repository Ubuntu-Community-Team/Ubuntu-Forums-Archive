---
title: "BOOT FAILED: Failed to start Remount Root and Kernel File Systems"
date: 2018-03-29
forum: General Help
---

### Post by captainbeer on 2018-03-29
Hi when I'm trying to start ubuntu it says that it Failed to start Remount Root and Kernel File Systems. I've tried to start it in recovery mode and typed: sudo fsck -f /dev/sda6 but it didn't work. My partitions look like this:

/dev/sda1 - EFI System
/dev/sda2 - Microsoft reserved
/dev/sda3 Microsoft basic data
/dev/sda4 Microsoft basic data
/dev/sda5 Windows recovery enviroment
/dev/sda6 Linux filesystem
/dev/sda7 Linux swap

please help, I'm pretty desperate..

---

### Post by oldfred on 2018-03-29
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

You may need fsck on your / partition.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

