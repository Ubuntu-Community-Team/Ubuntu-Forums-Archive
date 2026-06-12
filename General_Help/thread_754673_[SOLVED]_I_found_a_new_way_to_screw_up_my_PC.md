---
title: "[SOLVED] I found a new way to screw up my PC"
date: 2008-04-14
forum: General Help
---

### Post by Jive Turkey on 2008-04-14
I have a windows partition that couldnt mount at install time because of a dirty shutdown. I have since shut it down cleanly and attempted to mount it to "/windows" using the context menu>volume>Settings and putting /windows in as the mountpoint.  turns out you arent supposed to put any leading '/' in the mount point field and now I cant mount it at all nor can I access the volume properties via the context menu because of invalid  mount options.  I cant seem to find where the invalid setting was stored but I really want to mount the volume.  I should have used fstab but that gui looked so easy.

---

### Post by sekinto on 2008-04-14
This is what I would do.

Make the directory you want to mount it in, "sudo mkdir /media/windows" for example.
Type in the command "sudo nano /etc/fstab"
Go to the end of the file and add something like this:
```
UUID=<UUID of partition>   /media/windows   ntfs   defaults   0   3
```
To find out the partition's UUID you can do "ls -l /dev/disk/by-uuid/"
You might want to change the 3, not sure though.

---

### Post by Jive Turkey on 2008-04-14
> **sekinto said:**
> This is what I would do.

Make the directory you want to mount it in, "sudo mkdir /media/windows" for example.
Type in the command "sudo nano /etc/fstab"
Go to the end of the file and add something like this:
```
UUID=<UUID of partition>   /media/windows   ntfs   defaults   0   3
```
To find out the partition's UUID you can do "ls -l /dev/disk/by-uuid/"
You might want to change the 3, not sure though.
that worked like a charm, thanks.

---

### Post by sekinto on 2008-04-14
No problem, just learned how to do that earlier today myself. I mean I always knew how to edit the /etc/fstab file, but I didn't know how to find out the UUID of a partition.

---

