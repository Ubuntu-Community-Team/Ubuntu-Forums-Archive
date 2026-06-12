---
title: "Read Only File system problem"
date: 2014-09-05
forum: General Help
---

### Post by geeks2 on 2014-09-05
/dev/mapper/tmuat--vg-root / ext4 ro,relatime,errors=remount-ro,data=ordered 0 0

---------------------------

 I am using Ubuntu 12.04.4 LTS(Kernel version 3.11.0-15-generic), when i tried to create file in my home directory /home/user
I got the follwing error

$touch a
touch: cannot touch `a': Read-only file system

$sudo mount
sudo: unable to open /var/lib/sudo/user/1: Read-only file system
/dev/mapper/tmuat--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/usr/tmp on /tmp type ext4 (rw)
/home/user/.Private on /home/user type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=3951423444cb6100,ecryptfs_fnek_sig=e154d6ff1a7033bc)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.

$sudo cat /etc/mtab

sudo: unable to open /var/lib/sudo/user/1: Read-only file system
/dev/mapper/tmuat--vg-root / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /boot ext2 rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
/dev/loop0 /tmp ext4 rw 0 0
/home/user/.Private /home/user ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=3951423444cb6100,ecryptfs_fnek_sig=e154d6ff1a7033bc 0 0

$sudo cat /proc/mounts
sudo: unable to open /var/lib/sudo/user/1: Read-only file system
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=2011392k,nr_inodes=502848,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=809468k,mode=755 0 0
/dev/mapper/tmuat--vg-root / ext4 ro,relatime,errors=remount-ro,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
/dev/sda1 /boot ext2 rw,relatime,errors=continue,user_xattr,acl 0 0
overflow /tmp tmpfs rw,relatime,size=1024k,nr_inodes=493116 0 0
/dev/loop0 /tmp ext4 ro,relatime,data=ordered 0 0
/home/user/.Private /home/user ecryptfs ro,relatime,ecryptfs_fnek_sig=e154d6ff1a7033bc,ecryptfs_sig=3951423444cb6100,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs 0 0



$df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/tmuat--vg-root  144G  5.6G  131G   5% /
udev                         2.0G  4.0K  2.0G   1% /dev
tmpfs                        791M  268K  791M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         2.0G  4.0K  2.0G   1% /run/shm
/dev/sda1                    236M   36M  188M  17% /boot
overflow                     2.0G  4.2M  1.8G   1% /tmp
/dev/loop0                   2.0G  4.2M  1.8G   1% /tmp
/home/user/.Private       144G  5.6G  131G   5% /home/user

$dmesg
[3636030.945621] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-30]
[3636030.945957] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000000c])
[3636031.015792] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-30]
[3636031.016400] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000000c])
[3636031.016696] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-30]
[3636031.017053] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000000c])
[3636031.017136] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-30]
[3636031.017461] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000000c])




I found /dev/mapper/tmuat--vg-root / ext4 ro,relatime,errors=remount-ro,data=ordered 0 0 as ro. If this has been posted in the wrong forum , Kindly move it to the appropriate forum. Apologies for the inconvenience.
Can you plese help me to fix this issue. Thanks in advance.

---

### Post by Impavidus on 2014-09-05
Your file system has been mounted read-only. This may happen when some error occurs during access to the drive, to prevent further damage. I'd start with checking the health of the hard drive. You can remount the file system as read-write. Rebooting also works.

Make sure you have proper backups. You have an encrypted system. If the drive fails, there is no chance of recovering anything.

---

