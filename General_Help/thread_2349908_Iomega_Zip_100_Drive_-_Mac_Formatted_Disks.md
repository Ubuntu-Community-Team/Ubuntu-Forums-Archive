---
title: "Iomega Zip 100 Drive - Mac Formatted Disks"
date: 2017-01-19
forum: General Help
---

### Post by rebeltaz on 2017-01-19
I am trying to get an Iomega Zip 100 USB drive to work with Ubuntu. At first, the disk (which is Mac formatted) kept mounting as '/media/Zip 100' in a read-only state owned by root. I could write to the partition as sudo, but not as user. After inserting another (Mac formatted) disk in to the drive though, I found that that one mounted as '/media/untitled' so it's mounting the partition according to the volume label. OK, so looking at dmesg, I found that the actual partition is /dev/sdh4. So I added an entry to fstab to auto mount that when called to /media/ZipDisk. It tried to mount, but said that the filetype was unknown. Next, I tried gparted to remove the partition(s) and reformat the disk to something more useable - ext4 or ext2. As long as the fstab entry was active, I could work on sdh4, but if I disabled that entry, I could no longer operate on sdh4. 

Gparted shows four partitions - sdh1, sdh2, sdh3 and sdh4. The first three, sdh1-3, are listed as an unknown filetype and the sdh4 is listed as an hfs filetype. I can delete the sdh4 partition, but trying to delete the sdh1-3 partitions fails. I even tried adding fstab entries for those but that didn't help (didn't really think it would, just thought I'd try). So, I figured I'd just leave those three (they are only 5, 200 and 64kb anyway) and just create a new sdh4 partition formatted with ext4. Like I said, I can delete the partition (I already did on one disk) but trying to create a new partition fails. I tried ext2, ext4, fat16 and fat32. 

Oh, and fdisk doesn't recognize the partition table at all, so I cannot eve try to work with the disk through the command line.

So... long story short, how can I format a Mac formatted Zip disk to work with Linux?

---

### Post by ajgreeny on 2017-01-19
Try gparted again but go to the **Device ->Create partition table** menu entry and create a new PT.

Use the default ms-dos PT then in the unallocated space create a new partition in whatever filesystem you need; fat32 is the most useful if you still need to use it in Windows, Mac and Linux.

---

### Post by rebeltaz on 2017-01-19
Awesome! Worked like a charm! I knew it was something simple I was overlooking. Thank you!

---

### Post by rebeltaz on 2017-01-19
Crap... spoke too soon. I was able to format the disk, but I still can't mount it in a usable way.

Without any fstab entry related to the Zip drive, the disk will mount and I have no trouble reading from it. I cannot write to the disk however, unless I open the disc as a superuser. 

So I created a ZipDrive directory under /media, changed the owner and group to derek (me) and changed the permissions to 777. I then added ```
# /dev/sdh1 /media/ZipDrive auto rw,user,noauto,exec,umask=0,utf8 0 0
``` to fstab and the disc will no longer even mount, telling me:

```

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdh1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried ext4 (the format I used) instead of auto and it still won't mount. So what do I do now?

---

### Post by rebeltaz on 2017-01-31
bump?

---

### Post by QIII on 2017-01-31
Hello!

What happens if you just try 

```
defaults
```

for your mount options?

This is not a suggested solution, but a start at diagnosis.

---

### Post by rebeltaz on 2017-01-31
I am willing to try [almost] anything! Thank you.

I changed the line to:

```
 /dev/sdh1 /media/ZipDrive auto defaults 0 0
```

The disks still mounts, but it is also still mounting in read-only mode as a normal user with write permissions as a superuser. 

I try to eject the disk and it tells me that only the root has permission to unmount.

Is it possible that it has something to do with the way I formatted the disk? Would it be possible to format using gparted in such a way that only root could write to a disk? Just a thought...

---

