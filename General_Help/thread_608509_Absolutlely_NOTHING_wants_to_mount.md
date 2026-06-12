---
title: "Absolutlely NOTHING wants to mount"
date: 2007-11-10
forum: General Help
---

### Post by BVBBQ on 2007-11-10
hey all every time i try to mount anything i get a

"cannot mount the volume "IPOD" mount:wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program or other error in some cases useful into is found in syslog - try dmesg | tail
 or so 

so i did, 

[ 1296.720312] sda: assuming drive cache: write through
[ 1296.722171] SCSI device sda: 991232 2048-byte hdwr sectors (2030 MB)
[ 1296.723170] sda: Write Protect is off
[ 1296.723175] sda: Mode Sense: 68 00 00 08
[ 1296.723180] sda: assuming drive cache: write through
[ 1296.723183]  sda: sda1 sda2
[ 1296.725970] sd 7:0:0:0: Attached scsi removable disk sda
[ 1296.726023] sd 7:0:0:0: Attached scsi generic sg0 type 0
[ 1297.711036] FAT: Unrecognized mount option "usefree" or missing value
[ 1334.827235] FAT: Unrecognized mount option "usefree" or missing value

any thoughts?

---

### Post by Jose Catre-Vandis on 2007-11-10
Need a bit more info:

Looks like your ubuntu partition mounts :)

report back with output of :
```
sudo fdisk -l
```
```
cat /etc/fstab
```
```
df -Th
```
with device plugged in
and also what mount command are you using

---

### Post by adrpater on 2007-11-10
The solution posted here: 
[http://ubuntuforums.org/showthread.php?p=3707221](http://ubuntuforums.org/showthread.php?p=3707221)

worked for me:

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options , and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again.

---

