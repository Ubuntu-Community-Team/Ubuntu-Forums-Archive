---
title: "[SOLVED] Volume labels in 8.04"
date: 2008-05-24
forum: General Help
---

### Post by GurneyHalleck on 2008-05-24
I'm sure someone's already asked this question, but I've searched using several terms and I can't find what I'm looking for. So . . . 

Is it possible to tell Ubuntu 8.04 to label mounted volumes the same way that Ubuntu 7.04 and 7.10 used to label them?

It was very handy having mounted drives appear as /media/music, /media/share and so on, but Ubuntu 8.04 is offering cryptic names such as "68.1 GB Media" and "41.9 GB Media".

I've hunted around in the preferences, and in the options for fstab, but I don't see any way of reverting to the way things used to appear.

Has anyone solved this?

---

### Post by ibuclaw on 2008-05-24
[Here's a How-to in the Ubuntu Docs.]("https://help.ubuntu.com/community/RenameUSBDrive")

If you are trying to rename NTFS paritions:
```

sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sda1 newname

```

Regards
Iain

---

### Post by strabes on 2008-05-24
What if the partitions aren't ntfs?

---

### Post by ibuclaw on 2008-05-24
> **strabes said:**
> What if the partitions aren't ntfs?
[Follow the link...]("https://help.ubuntu.com/community/RenameUSBDrive")

> **tinivole said:**
> [Here's a How-to in the Ubuntu Docs.]("https://help.ubuntu.com/community/RenameUSBDrive")


It's got info on FAT, NTFS, ext, JFS, ReiserFS and XFS.

But let me guess... You use a UDF filesystem??? ;)

Regards
Iain

---

### Post by GurneyHalleck on 2008-05-24
Hello, tinivole.

I've relabeled the NTFS volume, but it is still showing up in Ubuntu as "36.7 GB Media" after a dismount and mount.

Is it really not possible to get 8.04 to show more useful labels for these volumes?

---

### Post by ibuclaw on 2008-05-24
> **GurneyHalleck said:**
> Hello, tinivole.

I've relabeled the NTFS volume, but it is still showing up in Ubuntu as "36.7 GB Media" after a dismount and mount.

Is it really not possible to get 8.04 to show more useful labels for these volumes?

Try unmounting the partition, THEN relabelling it.
I don't think it works on partitions the are currently mounted.

[EDIT]
Works for me...
```
sudo blkid /dev/sdb5
/dev/sdb5: UUID="6AB0419AB0416E1F" LABEL="**newlabel**" TYPE="ntfs" 

```
Although, I see your point (Gnome hasn't changed the name of it).

I'm about to reboot, see if that makes any difference.

Regards
Iain

---

### Post by ibuclaw on 2008-05-24
Yep...

Reboot and GNOME changes the name.
See attachment...

---

### Post by Jose Catre-Vandis on 2008-05-25
Just to confirm how this all works:

to find your volume locations
```
sudo fdisk -l
```

For ext2/ext3 volumes
```
sudo e2label /dev/sd? VolumeName
```

For ntfs volumes (after installing ntfsprogs)
```
sudo ntfslabel /dev/sd? VolumeName
```

Then reboot to see changes.

Why they took this functionality out I do not know!

---

### Post by GurneyHalleck on 2008-05-25
Thank you, tinivole, the reboot did it. And thanks for the link to the FAT renaming guide; most of my volumes are FAT32. (A misguided plan to have the files available to both Linux and Windows XP. But I haven't used any of the files in Windows XP since installing Feisty Fawn.)

---

### Post by ibuclaw on 2008-05-25
> **GurneyHalleck said:**
> Thank you, tinivole, the reboot did it. And thanks for the link to the FAT renaming guide.

Your Very Welcome Gurney Halleck.

> **GurneyHalleck said:**
> I haven't used any of the files in Windows XP since installing Feisty Fawn.
Good Man! :D

Regards
Iain

---

