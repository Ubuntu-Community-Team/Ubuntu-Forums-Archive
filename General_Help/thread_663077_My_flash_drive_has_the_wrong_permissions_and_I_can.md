---
title: "My flash drive has the wrong permissions and I can't change them!"
date: 2008-01-09
forum: General Help
---

### Post by -grubby on 2008-01-09
well I lost permissions for my flash drive. 
Let me explain:
So I had to reformat my flash drive (because the filesystem got corrupted) and for some reason the first computer I plugged it in to got full permissions to it (A linux computer btw)(I can't access it or change the permissions at all) and the user "lacey" (but the install of which lacey was a member is no longer running)  owns the whole drive. 
Under thunar, root and "other users" dont' have ANY permissions (everybody but Lacey can't see the flash drive at all (but as I told you the user "lacey" doesn't exist anymore)) . And That user can't change them. for some reason, the flash drive works on all windows installs I've tried so far. I've tried 
```
sudo chown 777 /media/disk/
``` 
and it didn't work (isn't that because the user "lacey" acts as root under sudo and that root apparently didn't have any permissions?)

---

### Post by ajmorris on 2008-01-09
if you are mounting the flash disk via fstab, add to the options section:
```
users
``` this means that all users in the users group can mount and r/w to the flash disk

also, what format is the flash disk?

---

### Post by nikoPSK on 2008-01-09
Unfortunately this happens all the time with FAT/ NTFS partitions. I would format (again), as long as it doesn't have any important files. 

Best,
nikoPSK

---

### Post by nikoPSK on 2008-01-09
Another thing, you have to set permissions at the time of mount. :popcorn:

---

### Post by bodhi.zazen on 2008-01-09
Depends on the file system.

If it is linux

sudo chown user.group ...

then 

chmod 777 ...

If it is FAT/NTFS you need to set permissions in fstab or mount

mount /dev/xxx /mount/point -o uid=1000,gid=100,umask=007

---

### Post by -grubby on 2008-01-09
yes it is FAT32

---

### Post by -grubby on 2008-01-09
> **nikoPSK said:**
> Unfortunately this happens all the time with FAT/ NTFS partitions. I would format (again), as long as it doesn't have any important files. 

Best,
nikoPSK

the thing is that I tried to format a couple times and it still didn't work. I even tried a linux filesystem but if that ended up working than it wouldn't matter because I have to communicate with Windows 2000 computers (do they support NTFS?)

---

### Post by bodhi.zazen on 2008-01-09
```
sudo umount /media/disk
sudo mount /dev/xxx /media/disk -o uid=1000,gid=100,umask=007
```

fstab:

> /dev/xxx /media/disk vfat auto,users,uid=1000,gid=100,umask=007 0 0

change /dev/xxx to your device (/dev/sdb1 perhaps)

edit fstab with :```
gksu gedit /etc/fstab
```

---

### Post by -grubby on 2008-01-09
hmm that's weird. Now it works. I think it may have been because I used it on a windows 2000 computer. But I don't have any idea

---

### Post by nikoPSK on 2008-01-09
> **nathangrubb said:**
> hmm that's weird. Now it works. I think it may have been because I used it on a windows 2000 computer. But I don't have any idea

Well, glad every things hunkey dorey. You got your files all right? no corruptions?

---

