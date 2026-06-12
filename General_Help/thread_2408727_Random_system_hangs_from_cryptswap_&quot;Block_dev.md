---
title: "Random system hangs from cryptswap &quot;Block device required&quot;"
date: 2018-12-22
forum: General Help
---

### Post by llamalord2 on 2018-12-22
So my 18.10 system (originally installed as 18.04) has the default Ubuntu partition setup for choosing to use the whole disk, but I chose the option to encrypt the drive.

Now (and before when the system was 18.04) the system completely hangs at random seeming intervals. Even Ctrl + SysRQ + RSEINUB does nothing. Every time it happens, the old syslog shows the same thing at the end:
```

Dec 22 00:00:35 Merovingian systemd-cryptsetup[6076]: crypt_init() failed: Block device required
Dec 22 00:00:35 Merovingian systemd[1]: systemd-cryptsetup@cryptswap1.service: Main process exited, code=exited, status=1/FAILURE
Dec 22 00:00:35 Merovingian systemd[1]: systemd-cryptsetup@cryptswap1.service: Failed with result 'exit-code'.
Dec 22 00:00:35 Merovingian systemd[1]: Failed to start Cryptography Setup for cryptswap1.
Dec 22 00:00:35 Merovingian systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
Dec 22 00:00:35 Merovingian systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
Dec 22 00:00:35 Merovingian systemd[1]: dev-mapper-cryptswap1.swap: Job dev-mapper-cryptswap1.swap/start failed with result 'dependency'.
Dec 22 00:00:35 Merovingian systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
```

Here's the output of lsblk:
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0 232.4G  0 part /

```

and the contents of cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=dabc38a5-afcf-4cec-be94-9ee49972e248 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=7451-D64A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

How would I go about troubleshooting this?
Thanks!

---

