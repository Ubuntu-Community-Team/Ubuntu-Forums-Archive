---
title: "My external storage device has turned read only!!"
date: 2007-04-09
forum: General Help
---

### Post by haaskaa on 2007-04-09
I have an external storage device "Packard Bell Store & Save" (hard drive - not flash), that I use to store media files. It has a USB connection to my laptop. However I just installed feisty on my newest laptop, and when I go to /media/PB_SAVE/  where the external disc correctly gets mounted, it is now READ-ONLY, and root has no permissions to change that.

When I plug it into my older laptop (running Xubuntu edgy) the same thing happens. It gets mounted in /media/ but as a READ-only disc.

If anyone knows why this happens and how I can change it, I'll appreciate some help.

---

### Post by Swab on 2007-04-09
What filesystem is on the external disk?   If it's NTFS, then this is normal.  You might want to look into ntfs-3g

---

### Post by taurus on 2007-04-09
What is the filesystem on that external drive?

---

### Post by haaskaa on 2007-04-09
> What is the filesystem on that external drive?

In system monitor the system is listed as type "vfat". The rest of my system is ext3.

It has been working perfectly since I bought it some time ago. But this morning I tried to delete some files from it but I get an error message saying it is read only. It has NOT been read-only before, so that made me think maybe it's a permissions issue.

---

### Post by Swab on 2007-04-09
This might seem stupid, but is there a write protect switch on the drive?

---

### Post by taurus on 2007-04-09
Try

```
sudo umount /media/PB_SAVE
sudo mount -t vfat /dev/sda1 /media/PB_SAVE -o iocharset=utf8,umask=000
ls -la /media/
```

---

### Post by haaskaa on 2007-04-09
Mounting like this:

```
sudo mount -t vfat /dev/sda1 /media/PB_SAVE -o iocharset=utf8,umask=000
```

.. makes ls -al return this for the /media/ folder:

```
drwxrwxrwx 12 root root 32768 1970-01-01 01:00 PB_save
```

However, trying to delete a file from PB_save gives this error message:

```
rm: cannot remove `somefile.txt': Read-only file system
```

I'm lost at this point.

---

