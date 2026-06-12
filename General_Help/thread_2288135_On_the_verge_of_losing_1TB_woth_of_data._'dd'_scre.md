---
title: "On the verge of losing 1TB woth of data. 'dd' screwed me"
date: 2015-07-24
forum: General Help
---

### Post by EzioAuditore on 2015-07-24
Ok right now I'm really terrified. Its my friend's HDD I asked for some backup puposes but now I'm totally screwed.. 

I was gonna erase my whole HDD for preparing it for dual boot setup. So thought to take a backup of the pre-created factory recovery partition to my friend's external HDD..

I used the 'dd' command thinking it will create an image file of the intended partition.. 
I used the following code
```
dd if=/dev/sda1 of=/dev/sdd1
```

/dev/sda1 being the recovery partition
/dev/sdd1 being the external HDD

After the completion of the operation I realised that the external HDD has been overwritten with the recovery partition's image..

So, how do I recover the data? Is there any hope of it even? 
I'll literally be screwed if it doesn't get back to the way it was before..

Please show me the light ..... ](*,)](*,)](*,)](*,)

---

### Post by v3.xx on 2015-07-24
Try testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2015-07-24
dd's nickname is data destroyer. It should be the last alternative you use to copy anything. But you can use it to create a file, if you had told it that. I found it better to just buy new flash drives and copy using Windows own tools & Dells own tools to the flash drives for my backups.

It does an exact sector for sector copy of whatever you told it to copy. And it copies empty data also. So sdd1 was totally overwritten with sda1. 
Only if sda1 is  smaller than sdd1 will some data beyond the size of sda1 be still in sdd1's partition. And that probably will not have file names & structure. You then may need photorec.
 
With photorec, it scans drive for anything that looks like a file. It only will have extension based on file type. You need another drive of a size that will hold all the data and it recovers delete files also, so more data than you may think. Best to have same size drive. 
It took me days to compare files recovered to may last backup and because it recovered deleted files I had many compares. And I only lost a smaller folder with mostly text files. But it recovered entire drive. Or oldfred backs up more often.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by v3.xx on 2015-07-24
A quick question oldfred :)

I haven't had to use testdisk in years (knock on wood) and never used photorec.

Is photorec the better product?

---

### Post by EzioAuditore on 2015-07-24
> **oldfred said:**
> dd's nickname is data destroyer. It should be the last alternative you use to copy anything. But you can use it to create a file, if you had told it that. I found it better to just buy new flash drives and copy using Windows own tools & Dells own tools to the flash drives for my backups.

It does an exact sector for sector copy of whatever you told it to copy. And it copies empty data also. So sdd1 was totally overwritten with sda1. 
Only if sda1 is  smaller than sdd1 will some data beyond the size of sda1 be still in sdd1's partition. And that probably will not have file names & structure. You then may need photorec.
 
With photorec, it scans drive for anything that looks like a file. It only will have extension based on file type. You need another drive of a size that will hold all the data and it recovers delete files also, so more data than you may think. Best to have same size drive. 
It took me days to compare files recovered to may last backup and because it recovered deleted files I had many compares. And I only lost a smaller folder with mostly text files. But it recovered entire drive. Or oldfred backs up more often.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Well the source partition is of only 367MB.. So, that means I still have a shot at getting the rest of it back?
And yeah I've got 1TB internal HDD to recover to..

---

### Post by oldfred on 2015-07-24
Testdisk and photorec are two products from same folks.

Testdisk is more to recover partitions, and its deeper search can recover data if file structure is still in partition. Not sure if every superblock has what is needed to restore file structure or if files names are only at beginning of drive.

Photorec is a last resort as it just scans drive looking for anything that is a file, but by type. It found all my .txt files as .txt but without names. And then I had a huge task to sort mostly by size and then look for data in each file. Because it looks for any data, it finds the files that end with ~ or backups and even the previous now deleted files. For text files I saved many times it found many files, but I had no way to know which was most current except by manually comparing each file to last backup.

---

### Post by v3.xx on 2015-07-24
As usual, a perfect explanation.

Thanks :)

---

