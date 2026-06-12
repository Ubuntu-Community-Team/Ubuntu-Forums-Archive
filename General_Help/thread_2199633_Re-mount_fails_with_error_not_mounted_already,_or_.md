---
title: "Re-mount fails with error not mounted already, or bad option for read-only /"
date: 2014-01-15
forum: General Help
---

### Post by rao.subba.venkata on 2014-01-15
Hi,

I have created an USB based read-only root file system based on the instructions from following link.
I used instruction given under section overlayfs

[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

This is perfectly working. Under some heavy load, when I try to mount the /mnt/root-ro partition in
read-write mode temporarily to update a file for persistence, I get following error.

mount: /mnt/root-ro not mounted already, or bad option

This doesn't happen always. Once it happens, it happens every time till I reboot the system.

Command I use is as follows.

sudo mount -o remount,rw /mnt/root-ro
copy the file (e.x.: sudo cp /usr/local/sbin/test to /mnt/root-ro/usr/local/sbin)
sudo mount -o remount,ro /mnt/root-ro

First command remounts /mnt/root-ro in RW mode and third command in RO mode back.

Can somebody in the forum advice me why this happens ?

Thanks,
Subbarao

---

### Post by jeanjd63 on 2014-01-15
Hello 
What is the result of the command :
**mount**

---

### Post by rao.subba.venkata on 2014-01-16
overlayfs-root on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
[B]/dev/sdc1 on /mnt/root-ro type ext4 (ro,relatime,user_xattr,acl,barrier=1,data=ordered,commit=0)
[/B]tmpfs-root on /mnt/root-rw type tmpfs (rw,relatime,size=1232896k)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb on /disk2 type ext4 (rw,commit=0,_netdev)
/dev/sdc2 on /home type ext4 (rw,commit=0)
/dev/sda1 on /disk1 type ext4 (rw,commit=0,_netdev)

---

