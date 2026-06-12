---
title: "Help! I used mkdosfs and formatted the wrong drive!"
date: 2007-09-09
forum: General Help
---

### Post by matthewdhandley on 2007-09-09
Help me! I was trying to format a small USB stick for booting wolfix linux, using mkdosfs, and I accidentally typed:
> mkdosfs -F 32 /dev/sda1
The dev was supposed to be sdb1. sda1 was my 250GB external hard drive, which was full of all my pictures, videos, and pretty much all my data I ever needed. I have not touched the drive, or written anything to it since I relaized what happened, and I'm hoping there is some way to recover the data. If anyone has any idea PLEASE help. My whole life was on that drive.

---

### Post by SPr on 2007-09-09
:(

I may well be mistaken here but I don't think you can format a drive that is mounted. So if the external drive was mounted you could be lucky.

---

### Post by matthewdhandley on 2007-09-09
I unmounted it. The first time I ran mkdosfs on sda1 it gave me an error that the drive was mounted. So I unmounted sda1, and re-ran mkdosfs. :(

---

### Post by SPr on 2007-09-09
:(

If there are no undelete programs for MSDos file systems in Linux do you have access to a PC running Windows? I don't know whether files can be undeleted after a format though.

---

### Post by merlinus on 2007-09-09
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Alex1770 on 2007-09-09
Sorry to say, but this is looking pretty bad. (From what you say, I'm assuming there is no backup to revert to.)

How much time did it spend formatting the drive? (Just trying to tell whether mkdosfs writes over large amounts of the disk, or just bits of it. If it only trashed bits of it, then there is more chance of recovery, but it still may be very hard.)

What filesystem (FAT32, ext3, ...) was it using before it was accidentally formatted?
E.g., if it was using ext3, then you could try googling ext3 recovery. It's not going to be easy though. ext3 breaks up files into lots of little bits and distributes them over the disk. The chances are that a lot of the bits are still there, but you need to figure out how to piece them back together. If you are lucky, someone has written a clever utility to do this.

I'm not sure this will work, but if you get another hard disk of exactly the same model and size then you might be able to blindly copy the contents of the old one on to the new one by an operation like dd if=/dev/sda of=/dev/sdx (replacing sdx with new disk). The advantage of this would be that you could experiment on the new disk without further damaging the old data, e.g., by sending it off to someone offering disk recovery services.

---

### Post by matthewdhandley on 2007-09-09
> **Alex1770 said:**
> How much time did it spend formatting the drive? (Just trying to tell whether mkdosfs writes over large amounts of the disk, or just bits of it. If it only trashed bits of it, then there is more chance of recovery, but it still may be very hard.)
It only took a few seconds. That's why I'm assuming it simply re-wrote the partition table and the data itself is still there.

> What filesystem (FAT32, ext3, ...) was it using before it was accidentally formatted?
It was FAT32

> I'm not sure this will work, but if you get another hard disk of exactly the same model and size then you might be able to blindly copy the contents of the old one on to the new one
Not sure I can afford another $150 drive right now.

::sigh:: It looks like I'm running out of options. TestDisk found thousands of files, but they all have gibberish names and have lost their extensions. It will take a lot of guesswork and testing to recover even a modest number of files that way.

---

### Post by Alex1770 on 2007-09-09
> **matthewdhandley said:**
> It only took a few seconds. That's why I'm assuming it simply re-wrote the partition table and the data itself is still there.


It was FAT32


Not sure I can afford another $150 drive right now.

::sigh:: It looks like I'm running out of options. TestDisk found thousands of files, but they all have gibberish names and have lost their extensions. It will take a lot of guesswork and testing to recover even a modest number of files that way.

Well it may not be so bad if it only took a few seconds and it was originally FAT32. It's not possible to write to a large proportion of a 250GB disk in a few seconds. Don't give up until you've read advice from someone more knowledgeable about this than me. Try googling FAT32 recovery.

---

### Post by SPr on 2007-09-10
Did you just use TestDisk?

Linked indirectly from the link Merlinus posted is this page which is what you want [www.cgsecurity.org/wiki/PhotoRec](www.cgsecurity.org/wiki/PhotoRec) . It doesn't find just photos but also a long list of other files ([www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)).

---

