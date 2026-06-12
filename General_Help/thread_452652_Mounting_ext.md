---
title: "Mounting ext"
date: 2007-05-23
forum: General Help
---

### Post by xodeus on 2007-05-23
Hi there.
I've tried to mount an ext3 partition on another harddrive writeable by me as user.
At the installation I chose it ti be mounted as Shared and I'm able to find it in /media/Shared but it's not writeable by me.
Then I've searched this forums and found out that if I do this trick it should make it writeable but with no luck:
```
sudo chown -R mariusz:mariusz /media/Shared
```

So how do I do it properly? Is it possible through fstab?
If yes, then how?

Here are some outputs:
```
mariusz@ubuntu:~$ ls -la /media/
total 24
drwxr-xr-x  6 root root 4096 2007-05-23 20:56 .
drwxr-xr-x 21 root root 4096 2007-05-16 20:05 ..
lrwxrwxrwx  1 root root    6 2007-05-16 19:53 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-05-16 19:53 cdrom0
lrwxrwxrwx  1 root root    7 2007-05-16 19:53 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-05-16 19:53 floppy0
-rw-r--r--  1 root root   48 2007-05-23 20:56 .hal-mtab
--wsr-x---  1 root root    0 2007-05-16 18:20 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2007-05-23 19:38 iso
drwxrwxr-x  1 root   80    6 2007-05-14 23:45 Share

```
```
mariusz@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a72f7e6f-25ca-4c66-a3e6-ad9cda53b1eb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1c199fb5-ef2c-4b89-bbf6-b29f22707128 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
```
mariusz@ubuntu:~$ more /etc/mtab 
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
/dev/sdb1 /media/Share hfsplus rw,nosuid,nodev 0 0

```
Hope that someone can help.

---

### Post by vtel57 on 2007-05-23
When you change ownership of the Shared directory, you're only changing the ownership of the directory itself. When you mount using temp Root privileges (sudo), you can only access the contents of the Shared folder as Root. If you want to be able to read/write/execute that partition that you're mounting, you'll have to place an entry for it in the fstab.

What partition are you trying to mount and access?

```
 $ sudo fdisk -l
```

---

### Post by xodeus on 2007-05-24
```
mariusz@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14569   117025461   83  Linux
/dev/sda2           14570       14946     3028252+   5  Extended
/dev/sda5           14570       14946     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14946   120053713+  83  Linux

```
It's the /dev/sdb1
Can U please help me with a fstab entry?

---

### Post by vtel57 on 2007-05-24
Sure. Here you go... try this:

```
/dev/sdb1     /media/Shared     ext3     rw,user,noauto     0     0
```

I'm mounting it in your /media/Shared directory that you spoke of earlier. With this entry in your fstab, you should be able to mount as a user from the graphic interface or from the command line: $sudo mount /dev/sdb1.

For future reference, here's an excellent tutorial on fstab:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Luck!

---

