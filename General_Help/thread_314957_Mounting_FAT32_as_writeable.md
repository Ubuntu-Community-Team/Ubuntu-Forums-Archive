---
title: "Mounting FAT32 as writeable"
date: 2006-12-08
forum: General Help
---

### Post by skewray on 2006-12-08
I have been trying to mount a FAT32 file system as writeable, without success. I am using the xubuntu live disk, and doing:

% sudo sh
# mkdir /test
# chmod a+rwx /test
# mount -o umask=000 /dev/sda1 /test

I can read the filesystem fine, but when I try to create a file, I am informed that the filesystem is read only. What am I missing?

Thanks,

Brian

---

### Post by bodhi.zazen on 2006-12-08
First unmount the device, ```
sudo umount /dev/sda1


then mount like this:[code]sudo mount /dev/sda1 /test -o umask=000
```

You will need the sudo unless you have an entry in fstab.

What are you trying to do?

---

### Post by skewray on 2006-12-08
That is the same thing as what I did.  "sudo sh" runs all the following commands as root.  The file system mounts up without complaint.

I don't understand the question about what I am trying to do.  I am trying to mount the partition in such a way that I can write to it.

Brian

---

### Post by strabes on 2006-12-08
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by bodhi.zazen on 2006-12-08
Why as a script (as opposed to an entry in fstab or directly with the mount command) ? And why not mount in /mnt or /media ?

At any rate, can you post:
```
sudo fdisk -l
```

and 

```
ls -la / | grep test
```

Last, is your usb device read-only (some have an external switch) or ntfs ?

---

### Post by skewray on 2006-12-08
I found the problem.  (A) I am stupid, and (B), the partition is actually NTFS, not FAT32.  I will need to put ntfsprogs on a USB stick, fire up the ubuntu live disk, install ntfsprogs from the USB stick, and then mount the SCSI NTFS disk.  Whew!

Thanks!

---

### Post by bodhi.zazen on 2006-12-08
Try ntfs-3g: [ntfs-3g](http://ubuntuforums.org/showthread.php?&t=217009)

---

### Post by BarFly on 2006-12-13
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2           11998       12161     1317330    5  Extended
/dev/hda3            9448       11997    20482875    b  W95 FAT32
/dev/hda5           11998       12161     1317298+  82  Linux swap / Solaris

I am dual booting XP and Ubuntu on separate HDD's.  Obviously, I created a partition to swap files (from the above).  I do not know how to access the FAT partition in Ubuntu.  How do I get Edgy to automatically read that partition?

Thanks.

---

### Post by taurus on 2006-12-13
Edit your /etc/fstab with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda3  /media/windows  vfat  iocharset=utf8,umask=000  0  0
```
Save it and now create a mount point and mount it.

```
sudo mkdir /media/windows
sudo mount -a
df -h
```

---

### Post by skewray on 2006-12-19
> **bodhi.zazen said:**
> Try ntfs-3g: [ntfs-3g](http://ubuntuforums.org/showthread.php?&t=217009)

nfs-3g won't work, for suble reasons.  I was trying to use the live disk, but I think nfs-3g requires a reboot after install.  Am I  wrong?

Brian

---

