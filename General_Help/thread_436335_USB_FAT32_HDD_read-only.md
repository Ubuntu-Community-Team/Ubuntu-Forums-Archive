---
title: "USB FAT32 HDD: read-only???"
date: 2007-05-07
forum: General Help
---

### Post by bogl on 2007-05-07
I've read the threads on USB HDD problems generally, but no-one seems to have  had my current issue.

My USB HDD has suddenly become read-only - and I can't seemingly change the permissions to alter this - unless I am missing something?

As per the subject: no NTFS issues here, the drive is formatted FAT32.

Thanks in advance,

bogl

---

### Post by taurus on 2007-05-07
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by locki85 on 2007-05-08
I have the same problem since today. FAT32 USB HDD read-only all of a sudden.

df -h gives me:

```
/dev/sdb1             112G   11G  102G  10% /media/EXTERN
```
(which is wrong, it should be something like 112G 72G 40G...)

---

### Post by taurus on 2007-05-08
> **locki85 said:**
> I have the same problem since today. FAT32 USB HDD read-only all of a sudden.

df -h gives me:

```
/dev/sdb1             112G   11G  102G  10% /media/EXTERN
```
(which is wrong, it should be something like 112G 72G 40G...)

Try

```
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/EXTERN -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by hanzomon4 on 2007-05-08
Yeah vfat or fat32 doesn't understand permissions so you have to specify it in /etc/fstb. I forgot how though.

---

### Post by bogl on 2007-05-08
df -h gives me

/dev/sdb1             150G   78G   72G  52% /media/SEA_DISC

and following

sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/SEA_DISC -o iocharset=utf8,umask=000
ls -la /media

gives me

drwxrwxrwx 30 root root    32768 1970-01-01 01:00 SEA_DISC


and still no write access.

Obviously, I'm not alone.

bogl

---

### Post by hanzomon4 on 2007-05-08
Try this```
sudo mount -t vfat -o user,rw,exec,umask=000 /dev/sdb1 /media/SEA_DISC
```
I guess you can add the utf8 thing```
sudo mount -t vfat -o user,rw,exec,iocharset=utf8,umask=000 /dev/sdb1 /media/SEA_DISC
```

---

### Post by bogl on 2007-05-08
> **hanzomon4 said:**
> Try this```
sudo mount -t vfat -o user,rw,exec,umask=000 /dev/sdb1 /media/SEA_DISC
```
I guess you can add the utf8 thing```
sudo mount -t vfat -o user,rw,exec,iocharset=utf8,umask=000 /dev/sdb1 /media/SEA_DISC
```

Still not writable, I'm afraid.

I'm bewildered!

---

### Post by locki85 on 2007-05-08
Did not work for me either. That's a really bad time to happen, because I need the HDD for file-exchange with my windows-partition, and its my only possibility to do that!

---

### Post by anaconda on 2007-05-08
do you have r/w rights to the folder you mount yout fat32 partition to?

try with root rights.
```
sudo nautilus
``` 

can you write to it using root rights?

---

### Post by locki85 on 2007-05-08
Read only also with root rights.

By the way, I don't mount the hdd myself, it gets automatically mounted when plugged in... When I unplug it, the folder gets deleted, too

---

### Post by bogl on 2007-05-08
> **anaconda said:**
> do you have r/w rights to the folder you mount yout fat32 partition to?

try with root rights.
```
sudo nautilus
``` 

can you write to it using root rights?

Nope.  

Time to file a bug???

---

### Post by hanzomon4 on 2007-05-08
Try changing umask=000 to umask=777

---

### Post by bogl on 2007-05-08
> **hanzomon4 said:**
> Try changing umask=000 to umask=777

Still not writable with Nautilus as root.

---

### Post by locki85 on 2007-05-09
From my XP-partition I encountered two corrupt folders: one I created, and seemingly failed to delete properly, and one created by the windows system, i think (G:/system volume information/_restore{651EC9BF-6D7D-4889-9FCD-5F19F16AB28E}).

Because of the last folder being corrupt, I could not defragment the hard disc.

I think the problem might have to do something with that!

---

### Post by locki85 on 2007-05-14
Any further ideas?

---

### Post by bogl on 2007-05-14
When time & opportunity permit, I shall simply back up all of the data and reformat the disk.  

Still, obviously it's a problem a number of people are having.  I also think it might be time to file a bug report.

Unless anyone else has any ideas?

In short...

BUMP

---

### Post by locki85 on 2007-05-17
Okay, I solved the problem for me.

I did an intense filesystem-check on Windows XP (Right-click on the HDD in Explorer -> Properties -> Extras -> Filesystem-check -> Check both options -> Start). Duration about 2 hours, problem solved after that.

Why the problem occured: Probably when I hibernated from windows with open files from the USB-Disc, Linux found corrupt files and canceled the writing-permission for security issues.

---

