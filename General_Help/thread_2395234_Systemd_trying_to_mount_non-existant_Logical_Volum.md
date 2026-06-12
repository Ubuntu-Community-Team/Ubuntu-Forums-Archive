---
title: "Systemd trying to mount non-existant Logical Volume"
date: 2018-06-28
forum: General Help
---

### Post by super1395 on 2018-06-28
There is no entry for it in /etc/fstab, and it no longer exists in LVM.

    Yet I see this in the syslog:

    > 
    Jun 28 07:36:58 hostname systemd[1]: dev-mapper-hostname \x2d\x2dvg\x2dsandbox.device: Job dev-mapper-hostname \x2d\x2dvg\x2dsandbox.device/start timed out.Jun 28 07:36:58 hostname systemd[1]: Timed out waiting for device /dev/mapper/hostname --vg-sandbox.
    Jun 28 07:36:58 hostname systemd[1]: Dependency failed for /mnt/sandbox.
    Jun 28 07:36:58 hostname systemd[1]: mnt-sandbox.mount: Job mnt-sandbox.mount/start failed with result 'dependency'.
    Jun 28 07:36:58 hostname systemd[1]: Dependency failed for File System Check on /dev/mapper/hostname --vg-sandbox.
    Jun 28 07:36:58 hostname systemd[1]: systemd-fsck@dev-mapper-hostname \x2d\x2dvg\x2dsandbox.service: Job systemd-fsck@dev-mapper-hostname \x2d\x2dvg\x2dsandbox.service/start failed with result 'dependency'.
    Jun 28 07:36:58 hostname systemd[1]: dev-mapper-hostname \x2d\x2dvg\x2dsandbox.device: Job dev-mapper-hostname \x2d\x2dvg\x2dsandbox.device/start failed with result 'timeout'.
    

    >  cat /etc/fstab

    # /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point> <type> <options> <dump> <pass>

    #Boot

    /dev/md0 /boot ext2 defaults 0 2

    #LVM

    /dev/mapper/hostname --vg-swap none swap defaults,swap 0 2


    /dev/mapper/hostname --vg-root / ext4 defaults,noatime,errors=remount-ro 0 1


    /dev/mapper/hostname --vg-home /home ext4 defaults,noatime 0 2

    

    > lvscan

    ACTIVE '/dev/hostname -vg/root' [236.60 GiB] inherit
    ACTIVE '/dev/hostname -vg/home' [3.64 TiB] inherit
    ACTIVE '/dev/hostname -vg/swap' [1.50 GiB] inherit
    
    How to I remove all traces of the removed logical volume? I've tried searching for x2dsandbox.device and x2dsandbox.service with no luck.


Edit: Issue fixed after reboots.

---

