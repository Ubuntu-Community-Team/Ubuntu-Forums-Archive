---
title: "Data recovery from corrupt hard drive"
date: 2018-02-05
forum: General Help
---

### Post by Timmoore001 on 2018-02-05
Ubuntu 16.04

Unfortunately hard disc suffered a power glitch.   I suspect most of the data is still intack, but unsure which app to use to get started ?

Any I ideas on best tool to try and sort a recovery ?

:  )

Tim

---

### Post by deadflowr on 2018-02-05
Is the disk still accessible?
Meaning, if you plug it in and run from a live cd/dvd/usb can you mount the disk, or even see it.

---

### Post by Timmoore001 on 2018-02-05
Master boot has given up...   I did see the files with something like g-parted..   but didn't make any notes.....:  (((

Could not go back into it...  so no clues there....  whoops  :    (((

---

### Post by oldfred on 2018-02-05
Does BIOS/UEFI show drive?
If not shown by BIOS, it will not be able to be mounted at all.

But if in BIOS, then you should be able to mount it.
You may be able to run fsck from live installer.
And should in Disks and icon in upper right corner check Smart Status on drive. 

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change examples shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

