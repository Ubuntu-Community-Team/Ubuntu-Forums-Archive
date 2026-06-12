---
title: "Partition to disk image?"
date: 2017-01-18
forum: General Help
---

### Post by bucker2 on 2017-01-18
So I have this right?  According to  ( [https://ubuntuforums.org/showthread.php?t=1390428](https://ubuntuforums.org/showthread.php?t=1390428) ) and ( [http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html](http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html) ) I should be able to easily create a exact disk image of my sda1 disk partition using the below code:
 ```
dd if=/dev/hda1 bs=1k conv=sync,noerror of=/home/directory/filename
```

If so, I have a couple of questions.  sda1 is actually the factory recovery partition of my laptop which originally had windows 7.  I want to have a separate backup for redundancy.

- What format does this output?
- Will this be the best way to achieve my goal of a backup recovery partition?  It looks like "reinstalling" the partition would be as simple as creating appropriate partition and using dd and basically reversing if and of files, right (with necessary file paths)?
- Is there anyway to turn this disk image into a bootable USB or DVD (well given the size, I guess not DVD but how about in theory)?

---

### Post by HermanAB on 2017-01-18
Err... No.

Don't use dd to read a disk and write to the same disk.  The result is bound to be rather disappointing.

---

### Post by sudodus on 2017-01-18
Welcome to the Ubuntu Forums :-)

***dd*** does what you tell it to do without questions. ***dd*** can do the job, but it is very easy to get something wrong, a minor typing error is enough, and you might destroy your family pictures.

***dd*** creates a file, which is an image of the drive or partition. Each byte is cloned as it is, so there is no extra formatting. Such files are often given the extension img: filename.img (but any file name will do.)

-o-

There are tools for cloning, that are safer, faster and easier to use correctly. I use [Clonezilla](http://clonezilla.org). It is easiest to restore from an image of the whole drive, but it is also possible to clone one or some of the partitions, and restore those partitions to the same place in the original drive.

A Clonezilla image is a directory with a number of files, and the large files are compressed. Clonezilla is smart, and copies only the used blocks (skips free blocks), which makes the process faster and the image smaller, particularly if there is a lot of free space in the file system. Clonezilla can {write to / read from} a local drive (typically a USB hard disk drive), and it can also work via a network and {write to / read from} a server.

It is important that you ***test, that your backup works***. Test with a new drive with at least the same size as the original one, that you can restore your system from the backup to the new drive, and that the computer works with the new drive instead of the original drive. Otherwise you may get an unpleasant surprise, when you really need the backup.

-o-

It the drives are formatted in the same way at the low level, you can turn this disk image into a bootable USB drive for linux. This is often the case, but not always. Particularly very big drives may be different from small and medium sized drives.

But Windows will not boot from USB.

---

