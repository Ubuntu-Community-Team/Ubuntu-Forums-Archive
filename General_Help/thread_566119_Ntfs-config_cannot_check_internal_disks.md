---
title: "Ntfs-config cannot check internal disks?"
date: 2007-10-03
forum: General Help
---

### Post by cd-r80 on 2007-10-03
I installed NTFS support to Xubuntu Feisty. But I cannot check internal drives support in ntfs-config it shows only grey. I can only browse partitions in Thunar, no write access. What is wrong?  Fstab?

---

### Post by dcstar on 2007-10-03
> **cd-r80 said:**
> I installed NTFS support to Xubuntu Feisty. But I cannot check internal drives support in ntfs-config it shows only grey. I can only browse partitions in Thunar, no write access. What is wrong?  Fstab?

Installed the ntfs-3g package and made the necessary adjustments to your /etc/fstab file ?

---

### Post by cd-r80 on 2007-10-03
No I have not made mods to fstab yet. What were they?  The partitions were FATs. I formatted them to NTFS. I think they are very wrong?

---

### Post by vanadium on 2007-10-03
In /etc/fstab, you need to change the file system type to "ntfs-3g". If you leave "ntfs", then Linux will mount using the default, read-only driver. If it concerns formar FAT partitions, then the file type will still be specified as "vfat". Change that to "ntfs-3g".

It might be wise for you to post your current /etc/fstab lines here, because it also might contain some file-system specific options that also would need to be changed.

---

### Post by cd-r80 on 2007-10-03
Not working yet... NTFS windows use other lang. than Ubuntu?
/etc/fstab:

proc /proc proc defaults 0 0
# Entry for /dev/hda7 :
UUID=59071f95-2e1b-49e4-b5f5-6586edb61290 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda9 :
UUID=0a9baec1-d26c-4044-a7c4-934af46c0de4 /home ext3 defaults 0 2
# Entry for /dev/hda10 :
UUID=5e054ce8-b0e4-47b4-aca3-29a326fb1216 /usr ext3 defaults 0 2
# Entry for /dev/hda8 :
UUID=7bd4dc4d-4a28-4878-8172-d6c21a735cb9 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/hda1 /media/c ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda5 /media/d ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda6 /media/e ntfs-3g defaults,locale=en_US.utf8 0 0

mount
<snip>
/dev/hda1 on /media/c type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hda5 on /media/d type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hda6 on /media/e type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by cd-r80 on 2007-10-03
No help. Also Automatix complains about apt based error...

---

### Post by cd-r80 on 2007-10-03
This worked! [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585) . Ntfsprogs. Just libntfs8 had to be libntfs9.
No suc. with ntfs-3g?

Well I take my word back! It does not work very well. cannot copy some files?

---

### Post by cd-r80 on 2007-10-03
/dev/hda1 /media/c ntfs-3g defaults,locale=en_US.utf8,gid=46 0 1
/dev/hda5 /media/d ntfs-3g defaults,locale=en_US.utf8,gid=46 0 1
/dev/hda6 /media/e ntfs-3g defaults,locale=en_US.utf8,gid=46 0 1

And it works (ntfs-3g). Was that last number one which made "default permissions"?
Or that gid?

---

### Post by vanadium on 2007-10-04
fstab must be reloaded for the settings to take effect: either "sudo mount -a" or restart the system. The last number in your fstab should be either 2 (have the drive checked) or 0 (have the drive not checked during startup). You should reserve "1"  for the root system ("check that file system before all the others").

---

### Post by cd-r80 on 2007-10-05
Yes, I reloaded that. And it works. Even scandinavian letters. Made first by some manual and all the files could not be copied because of the filenames. Ok, that last number was about checking... moving to number 2.

---

