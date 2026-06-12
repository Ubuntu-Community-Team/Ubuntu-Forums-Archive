---
title: "Adding Hard Drive to Edgy Server"
date: 2006-11-18
forum: General Help
---

### Post by ilushkin on 2006-11-18
Please help me to add the new (not empty) harddrive to Edgy Server.
I plug it in. It has NTFS file system on it. I'd like to earase it completely and make sure that this extra space will be added to my ftp folder. How do I do it?
I run fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2341    18804051   83  Linux
/dev/hda2            2342        2434      747022+   5  Extended
/dev/hda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/hdd: 8606 MB, 8606545920 bytes
255 heads, 63 sectors/track, 1046 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1045     8393931    7  HPFS/NTFS

---

### Post by evilc on 2006-11-18
The easy I found was to just use a dos boot disc and reformat the 2nd drive, make sure you pick the right disc as dos can't see either linux or ntfs. If unsure just disconnect your linux while using dos boot disc.

---

### Post by druhboruch on 2006-11-18
```
sudo fdisk /dev/hdd
```


delete partition - I think the option is d
Create new primary partition and alocate all space to it.
Write changes to disk I think the option is w

Back at the bash prompt:

```
sudo mk2fs -j /dev/hdd1
```

The last thing is to add the line to /etc/fstab

/dev/hdd1 /var/ftp         ext3    noatime         0       2

Instead /var/ftp select your mount point.

Thats it.

---

### Post by ilushkin on 2006-11-18
I did exacly how you suggested. Now it looks good, only one problem i experience: now the ftp folder contains the new, added hard drive. how do I add my original folder with the files in it?

> **druhboruch said:**
> ```
sudo fdisk /dev/hdd
```


delete partition - I think the option is d
Create new primary partition and alocate all space to it.
Write changes to disk I think the option is w

Back at the bash prompt:

```
sudo mk2fs -j /dev/hdd1
```

The last thing is to add the line to /etc/fstab

/dev/hdd1 /var/ftp         ext3    noatime         0       2

Instead /var/ftp select your mount point.

Thats it.

---

### Post by koenn on 2006-11-18
when you mount hdd to /var/ftp, this means the contents of /var/ftp will be whatever is on hdd (so: nothing ?)
therefore you can not have both the 'old' /var/ftp and the contents of the hdd drive in the same directory / mount point.

best unmount again; and when you switch to /var/ftp you should see your files again.
```

umount /dev/hdd
cd /var/ftp
ls

```

copy those files somewhere out of the way (eg home), 
mount hdd again, 
```

mount /dev/hdd /var/ftp

```
copy files back to /var/ftp (which is now your hdd drive)

---

### Post by ilushkin on 2006-11-18
i see now :) thanks. soflink probably would solve my isssue :)

---

