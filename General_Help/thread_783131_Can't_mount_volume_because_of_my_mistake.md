---
title: "Can't mount volume because of my mistake"
date: 2008-05-05
forum: General Help
---

### Post by venator260 on 2008-05-05
I was trying to get my music partition to mount when I boot, and instead of asking here, I messed around a bit, and now it won't boot.

When it mounted, I right clicked on it and under the volume and disk tabs, I defined the mount point as /media/HANGAR 18, where it mounts to when I tell it to mount, and where I have several programs to look for files (Rhythmbox, my desktop backgrounds, etc...). I tried to mount it again, and it won't work. And I can't get into those boxes again to fix my mistake. I've attached a screenshot of the error message. 

So, how can I fix this?

---

### Post by joshsmith on 2008-05-05
the error message looks pretty clear, you could probably work it out
it cant have a space in the name

---

### Post by venator260 on 2008-05-05
I can't figure out where to edit the path that I specified. I can't get back into the dialog boxes that I could when the drive was mounted. I had assumed that the space was a problem, the issue is that I can't figure out where to go to take out the space.

---

### Post by joshsmith on 2008-05-05
sudo gedit /etc/fstab

---

### Post by venator260 on 2008-05-05
I tried that, and the partition in question does not have an entry in that file.

---

### Post by joshsmith on 2008-05-05
sorry i see what you mean
you can always mount in manually, a quick search of google gave this as an example:
mount -t ntfs-3g /dev/partition_name absolute_path _of_folder_to_mount_in

---

### Post by venator260 on 2008-05-05
Modified that to suit my situation, running:  

```
sudo  mount -t vfat /dev/sdb4 /media/Hangar
```

worked just fine, and I was able to erase my mistake


Thanks.

---

