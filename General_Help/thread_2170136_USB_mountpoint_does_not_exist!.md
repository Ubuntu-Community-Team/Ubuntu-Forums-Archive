---
title: "USB mountpoint does not exist!"
date: 2013-08-25
forum: General Help
---

### Post by jon-zendatta on 2013-08-25
Hi All
I wish to mount a Fat32 format flashdrive.
```
/dev/sdb1: LABEL="jericho" UUID="3261-5257" TYPE="vfat" 

```
```
sudo mkdir /media/usb

```
Here is the entry in fstab.
```
UUID=3261-5257 media/usb vfat defaults,user,exec,uid=1000,gid=100,utf8,umask=000 0 0
```
Then I attempt mount.
```
mount: mount point media/usb does not exist

```
But if I mount this way it works
```
sudo mount -t vfat /dev/sdb1 /media/usb

```
```
 mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/usb type vfat (rw)

```
So is my fstab entry incorrect?:KS

---

### Post by Cheesemill on 2013-08-25
Yes it is, you are missing a /.

Your new line should read...
```
UUID=3261-5257 /media/usb vfat defaults,user,exec,uid=1000,gid=100,utf8,umask=000 0 0
```

Notice the / before media/usb.

---

### Post by jon-zendatta on 2013-08-30
Go that cheers Cheesemill.

---

