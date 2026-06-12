---
title: "floppy disk problem"
date: 2006-10-26
forum: General Help
---

### Post by Sabrage on 2006-10-26
When I click on Floppy 1 in file browser i get > Unable to mount the selected floppy drive. 
mount: /dev/ is not a block device

what does it mean? :confused:

---

### Post by chippy99 on 2006-10-26
Strange, but you could try the following tests
Check that the device file exists. Type 'ls /dev/fd0'
It should come back with /dev/fd0.

Check that you have an entry in /etc/fstab for your floppy drive. Type 'cat /etc/fstab | grep fd0' 
, should return something like
/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto 0 0
If not paste this line into your fstab file.

---

### Post by Sabrage on 2006-10-27
thanks chippy99,

here's what happened:> frank@frank-desktop:~$ ls /dev/fd0
/dev/fd0
frank@frank-desktop:~$ cat /etc/fstab | grep fd0
frank@frank-desktop:~$ 


when i opened fstab in gedit i got:> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ed32d971-c463-4334-a3dd-147fe362f359 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=020cf8ab-0442-4d0e-8f56-79aa1c93fb72 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


I tried to save it as a backup before I change it but did not have the permission?

---

### Post by nikhilk on 2006-10-27
I think the last line in your "/etc/fstab" is the culprit.
Open it using the following command from a terminal
```
gksudo gedit /etc/fstab
```
then change the last line to
"/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0"

---

### Post by Sabrage on 2006-10-27
hi nikhilk,

when I changed the last line then Floppy 1 disappeared from the file browser.......:confused:

---

### Post by chippy99 on 2006-10-27
If you type [COLOR="Green"]sudo mount /dev/fd0 /media/floppy[/COLOR] does thedisk get mounted ?

---

### Post by Sabrage on 2006-10-27
No I don't think so. After I entered my password I just got a blinking cursor (no prompt)......

---

### Post by chippy99 on 2006-10-27
That is normal, when it mounts it only gives you a message if it fails.
If you type "df" after mounting the floppy you should see a line that say something like
/dev/fd0                  1424        63      1361   5% /media/floppy0

Also you should be able to do ls /media/floppy to list the contents of the floppy disk.

---

### Post by Sabrage on 2006-10-27
this time i waited for something to happen after i typed my password, and after waiting a few minutes i got:> frank@frank-desktop:~$ sudo mount /dev/fd0 /media/floppy
Password:
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock
frank@frank-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             38843744   2912936  33957628   8% /
varrun                  127992        84    127908   1% /var/run
varlock                 127992         0    127992   0% /var/lock
procbususb               10240        84     10156   1% /proc/bus/usb
udev                     10240        84     10156   1% /dev
devshm                  127992         0    127992   0% /dev/shm
lrm                     127992     17580    110412  14% /lib/modules/2.6.17-10-generic/volatile
frank@frank-desktop:~$ after this, when i doubleclick the floppy 1 emblem in the file browser i still get unable to mount... thanks for trying chippy99 (I'm trying to get you to help me further :mrgreen: )

---

### Post by nikhilk on 2006-10-28
Well if you know what is the filesystem on the floppy, you can specify that in the mount command by using the switch -t.
e.g. To mount a ext2 formatted floppy the mount command will be
```
mount -t ext2 /dev/fd0 /media/floppy0
```

---

### Post by Sabrage on 2006-10-28
thanks nikhilk, i need to do some reading on this i think....

---

