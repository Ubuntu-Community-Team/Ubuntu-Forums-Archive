---
title: "Swap not mounting"
date: 2007-04-15
forum: General Help
---

### Post by adamadamant on 2007-04-15
Hi,

I've just recently installed feisty and I'm having a bit of a problem with it. My swap partition is not mounting on startup. The first time I noticed it I fixed it by doing 'mkswap' on the swap partition. But when I restarted the computer it was unmounted again and now thats not working.

When I do 'sudo mkswap /dev/sda6' I get
```
Setting up swapspace version 1, size = 1052798 kB
no label, UUID=29180ff0-102e-4f41-847c-9f73fd93b87a

```
which is what I got before when it worked, but now top still shows no swap.

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a2a5ff8b-346e-406c-89dd-a080fded4ec8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=CDCE-A815  /share          vfat    defaults,utf8,umask=005,gid=46 0       1
# /dev/sda1
UUID=403C21893C217AD4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=fdc93d77-fefb-453b-b496-74e5c353e8ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
My mtab:
```
/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/sda3 /share vfat rw,utf8,umask=005,gid=46 0 0
/dev/sda1 /windows ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=joe 0 0

```

Any ideas? 

Thanks,
Joe

---

### Post by bakavic on 2007-04-16
Do have a look at this thread : [http://ubuntuforums.org/showthread.php?t=400673&highlight=no+swap](http://ubuntuforums.org/showthread.php?t=400673&highlight=no+swap)

The 2nd post in the thread gives a solution (basically replace the UUID with the device name for swap in /etc/fstab). Not sure if the change will survive the reboot, though. I haven't reboot my system yet.

---

### Post by yabbadabbadont on 2007-04-16
```
UUID=fdc93d77-fefb-453b-b496-74e5c353e8ae none            swap    sw              0       0
```
Notice that the UUID listed in your fstab file for swap does not match the one printed out when you ran mkswap.  Either change the UUID in /etc/fstab to match the one that was printed out or change /etc/fstab so that the swap entry looks like this:
```
/dev/sda6 none            swap    sw              0       0
```
You will need to use sudo when editing the /etc/fstab file or you won't be able to save the changes.

---

### Post by adamadamant on 2007-04-16
I changed the uuid in fstab to match the one given by mkswap and it seems to be working now. 

Thanks.

---

