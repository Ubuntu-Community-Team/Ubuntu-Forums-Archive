---
title: "ubundu os partition size is taken as volume label"
date: 2008-05-12
forum: General Help
---

### Post by nathanv117 on 2008-05-12
I installed Lnx 7.10 in one logical partition and Lnx 8.04 in another logical partition of 10.2 gb for using both versions, switching thru grub.

When I bring up Lnx 7.10 (/dev/sda7), it is mounted on media  / and Other NTFS partitions are mounted  by the system with the volume label names as their mount point (media) names. The Lnx 8.04 (/dev/sda9) partition is mounted on the media named as "10.2 GB Media." How can I get a more meaningful media name like Lnx804 assigned to this partition. May be I have to mount it in fstab with UUID name as I do not know what dev id they will get. Now, how to get the UUID for this Lnx 8.04 partition media?

I am new to Linux/Unix and trying to grasp this mounting methods.

Thnaks

---

### Post by zenwalker on 2008-05-12
Edit /etc/fstab, and give the device as /dev/<xxx> instead of some UUID thing and the destionation as /mnt/<xxxx>. Before doing so, just say 
umount <mount points>

Then mount -a will mount all the things once again and in the respective dir names as u have specified.

---

### Post by nick_h on 2008-05-12
> Now, how to get the UUID for this Lnx 8.04 partition media?
If you want to find the UUID, type:
```
ls -al /dev/disk/by-uuid
```

---

### Post by nathanv117 on 2008-05-12
> **zenwalker said:**
> Edit /etc/fstab, and give the device as /dev/<xxx> instead of some UUID thing and the destionation as /mnt/<xxxx>. Before doing so, just say 
umount <mount points>

Then mount -a will mount all the things once again and in the respective dir names as u have specified.

Thanks. worked. Still I get on the desktop and places the disk icon with label "10.2 GB Media". Can not rename? Where is it coming from?

Appreciate your help.

---

### Post by nathanv117 on 2008-05-13
How to change the name of an Ubuntu partition? Hope that change in label will not destroy the contents!

---

### Post by nick_h on 2008-05-13
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by housam on 2008-05-13
Ignore it ...

it was the same as above

---

