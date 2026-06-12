---
title: "SD Card always mounts read only"
date: 2008-03-08
forum: General Help
---

### Post by Arenlor on 2008-03-08
I can't seem to get it to work, the original was:
```
/dev/mmcblk0p1 on /media/disk type vfat (ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```
I then did this:
```
arenlor@arenlor:~$ sudo mkdir /media/SDCARD
arenlor@arenlor:~$ sudo chown arenlor /media/SDCARD
arenlor@arenlor:~$ ls -la /media
total 36
drwxr-xr-x  5 root    root  4096 2008-03-08 19:00 .
drwxr-xr-x 21 root    root  4096 2008-03-08 18:55 ..
lrwxrwxrwx  1 root    root     6 2008-02-08 01:55 cdrom -> cdrom0
drwxr-xr-x  2 root    root  4096 2008-02-08 01:55 cdrom0
drwx------  3 arenlor root 16384 1969-12-31 19:00 disk
-rw-r--r--  1 root    root   105 2008-03-08 18:59 .hal-mtab
-rw-------  1 root    root     0 2008-03-08 17:42 .hal-mtab-lock
drwxr-xr-x  2 arenlor root  4096 2008-03-08 19:00 SDCARD
```
I then edited fstab:
```
# SDCARD
/dev/mmcblk0p1 /media/SDCARD vfat rw,user
```
I then umounted and mounted:
```
root@arenlor:/home/arenlor# umount /media/disk
root@arenlor:/home/arenlor# mount /dev/mmcblk0p1
mount: block device /dev/mmcblk0p1 is write-protected, mounting read-only
root@arenlor:/home/arenlor# mount
/dev/mmcblk0p1 on /media/SDCARD type vfat (ro,noexec,nosuid,nodev)
```
And ls -la again:
```
arenlor@arenlor:~$ ls -la /media
total 28
drwxr-xr-x  4 root root  4096 2008-03-08 19:05 .
drwxr-xr-x 21 root root  4096 2008-03-08 18:55 ..
lrwxrwxrwx  1 root root     6 2008-02-08 01:55 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-02-08 01:55 cdrom0
-rw-r--r--  1 root root     0 2008-03-08 19:05 .hal-mtab
-rw-------  1 root root     0 2008-03-08 17:42 .hal-mtab-lock
drwxr-xr-x  3 root root 16384 1969-12-31 19:00 SDCARD
```
chowning again:
```
arenlor@arenlor:~$ sudo chown arenlor /media/SDCARD
chown: changing ownership of `/media/SDCARD': Read-only file system
arenlor@arenlor:~$ ls -la /media
total 28
drwxr-xr-x  4 root root  4096 2008-03-08 19:05 .
drwxr-xr-x 21 root root  4096 2008-03-08 18:55 ..
lrwxrwxrwx  1 root root     6 2008-02-08 01:55 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-02-08 01:55 cdrom0
-rw-r--r--  1 root root     0 2008-03-08 19:05 .hal-mtab
-rw-------  1 root root     0 2008-03-08 17:42 .hal-mtab-lock
drwxr-xr-x  3 root root 16384 1969-12-31 19:00 SDCARD
```
And one last try:
```
arenlor@arenlor:~$ sudo chown arenlor /dev/mmcblk0p1
arenlor@arenlor:~$ sudo chown arenlor /media/SDCARD
chown: changing ownership of `/media/SDCARD': Read-only file system
arenlor@arenlor:~$ ls -la /media
total 28
drwxr-xr-x  4 root root  4096 2008-03-08 19:05 .
drwxr-xr-x 21 root root  4096 2008-03-08 18:55 ..
lrwxrwxrwx  1 root root     6 2008-02-08 01:55 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-02-08 01:55 cdrom0
-rw-r--r--  1 root root     0 2008-03-08 19:05 .hal-mtab
-rw-------  1 root root     0 2008-03-08 17:42 .hal-mtab-lock
drwxr-xr-x  3 root root 16384 1969-12-31 19:00 SDCARD
```
So now I'm out of ideas, anyone have a clue?

---

### Post by fragos on 2008-03-08
Placing an SD card in the card reader will automount RW unless you have told Ubuntu not to or if the SD has the write protect switch turned to protect.  It has been that way for some time.  Too much command line can be bad for you.

---

### Post by Arenlor on 2008-03-08
Thank you, I had accidentally turn on the switch.

---

