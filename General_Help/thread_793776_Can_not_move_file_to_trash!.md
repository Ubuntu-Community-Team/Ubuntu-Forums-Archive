---
title: "Can not move file to trash!"
date: 2008-05-14
forum: General Help
---

### Post by favadi on 2008-05-14
I have 3 partitions, 2 FAT32, 1 ext3. In Ubuntu, when I try to delete a file or a folder in FAT32 partitions, it say "Can not move file to trash!", but it work normally in ext3 partition. It's quite painful. Plz give me the way to fix that probleme?

---

### Post by nicedude on 2008-05-14
You probably don't have ownership of the files on this drive.

Investigate using the chown command to take ownership of things and you might also investigate your fstab file to see how these partitions are mounted at boot time located here -> /etc/fstab . Just research & backup the fstab file before making any changes so you can avoid or easily correct any goofs.

---

### Post by ubuscout on 2008-05-14
...have u tried by graphic console (nautilus) or by shell ? ...if console, which command have u used ?

---

### Post by mandrill on 2008-05-14
IMHO, I would fire up gparted and "see" how things are mounted. If they need
resizing or a different mountpoint, you can do that by running the live cd,
and gparted is already there. Change, move, re-size, pick different mountpoint, whatever. Also I agree that you probably should check out your fstab......this is an excellent guide to mounting, permissions, etc.... 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Benic on 2008-09-22
You can check out this [_thread_]("http://ubuntuforums.org/showthread.php?t=921404&highlight=mount+fat32+partition") that will show you how to mount a ntfs/fat32 partition and make it visible. After that, you add the UUID tag of your partition in fstab. In my case, that solved the problem.

---

