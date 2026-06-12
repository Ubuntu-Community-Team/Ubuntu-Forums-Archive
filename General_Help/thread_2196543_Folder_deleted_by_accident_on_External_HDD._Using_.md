---
title: "Folder deleted by accident on External HDD. Using Foremost to recover."
date: 2013-12-30
forum: General Help
---

### Post by RayArdia on 2013-12-30
Folder accidentally deleted from /dev/sdc1 was Pictures, size about 3.5GB. Contents were in folders for Years, subfolders Months, sub-subfolders Days, contents .jpg files.
My initial search produced the stdn response, so tried again with fdisk -lu

Output of sudo fdisk -lu (the bit thatt applies to the external HDD 'Phillips' (/dev/sdc1)) was:-

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ff48
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625137344   312568641   83  Linux
ray@ray-Aspire-5735:~$ cd /media/ray/Phillips

Then tried:-
*sudo foremost -i /dev/sdc1

then, to invoke foremost:-
foremost -t jpeg -i /dev/sdc1

...and away it went, producing all sorts of symbols in its output, it seems to 'find' more than just .jpeg files, and goes on and on for hours.Only way to stop it is closing Terminal and killing the process.

Clearly I'm doing something wrong but I don't know what.
Can anyone help me please?

---

### Post by bashiergui on 2013-12-30
According to this link you need to designate the new place ti write the recovered jpegs, which needs to be a separate drive. Sounds like you can have the destination on your main drive since the deleted files live on an external drive.
[https://help.ubuntu.com/community/DataRecovery#Foremost](https://help.ubuntu.com/community/DataRecovery#Foremost)

Farther up the page that link recommended making a copy of the deleted files onto a separate drive, that's a really good idea especially if you're new to this. If you muck around with the original and accidentally overwrite the deleted space then it will be gone forever. If you accidentally overwrite the copy you can just make another copy.

---

### Post by RayArdia on 2013-12-31
> **bashiergui said:**
> According to this link you need to designate the new place ti write the recovered jpegs, which needs to be a separate drive. Sounds like you can have the destination on your main drive since the deleted files live onsequently it is taking Home about an hour tock symbol on them and I don't know why, or what to do about it. load and show them all! an external drive.
[https://help.ubuntu.com/community/DataRecovery#Foremost](https://help.ubuntu.com/community/DataRecovery#Foremost)

Farther up the page that link recommended making a copy of the deleted files onto a separate drive, that's a really good idea especially if you're new to this. If you muck around with the original and accidentally overwrite the deleted space then it will be gone forever. If you accidentally overwrite the copy you can just make another copy.
Thank you. I really did try to follow the instructions given in the link you pointed to but I guess I don't have enough brain cells to hand to get it right! ....However, whilst browsing other items in that link I came across a reference to 'recoverjpeg', installed it and got an immediate result - it found over 73000 .jpeg items! 
Unfortunately it has dumped them in my Home folder, as individual items, consequently Home takes absolutely ages to load!
All the items have a lock symbol on their icon and I don't know why, or what to do about it. Any suggestions?
Thank goodness I had the sense not to write anything to my external HDD.

---

### Post by oldfred on 2013-12-31
If you just deleted partition, what does testdisk show?

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Are files you recovered set as ReadOnly?

---

### Post by RayArdia on 2014-01-01
[QUOTE=oldfred;12887963]If you just deleted partition, what does testdisk show?

All recovered files, some 72200 jpeg files are shown with a lock symbol (read-only I assume). The bulk are photographs from a deleted Pictures folder, but others seem to have been 'recovered from folders on my external drive which were in fact never lost. Since each type is simply shown as 'Image NNNNNN.jpeg' it is going to be a slow process to sort them out and replace them in their correct folders if I have to eyeball every one!

Three screenshots attached:-[ATTACH=CONFIG]249073[/ATTACH][ATTACH=CONFIG]249074[/ATTACH][ATTACH=CONFIG]249075[/ATTACH]

TestDisk is continuing to run in 'Search Deeper' mobe.

---

### Post by RayArdia on 2014-01-01
I should add that the third screenshot in my previous post is the 'tale-end' of the output from home ls. As you can see there are in fact 72467 recovered files listed.
It would seem taht the program Recoverjpeg has worked [U]too[U] well!

---

### Post by oldfred on 2014-01-01
Is the first NTFS partition shown by testdisk the one you deleted? I would then just restore that. It may need chkdsk but may also restore it enough to include file names.

JPEG files have internal data that will let you rename to date or order.
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by RayArdia on 2014-01-01
> **oldfred said:**
> Is the first NTFS partition shown by testdisk the one you deleted? I would then just restore that. It may need chkdsk but may also restore it enough to include file names.

JPEG files have internal data that will let you rename to date or order.
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

The NTFS partition is the one with Windows 7 in it. It was never deleted and all is well there.
The .jpeg files were cut,* instead of copied* from folder Pictures on  my external HDD  (/dev/sdc1 named Phillips) into /home/ray/Pictures. Subsequently, I had problems with partitions and after taking advice decided to use just 2 linux partitions, the existing Swap partition /sda2 and an enlarged /sda3. I thought that because sda3 was only being 'lengthened' that the Ubuntu installation was safe. EVEN after the warnings still thought all would be welland that because I was certain that I had made a copy of the whole of /home I was OK.
You may wonder how I forgot that I had moved Pictures - but I did. Of course the 'penny dropped' about a minute later!

I had hoped that all the exif files would still be intact if I was able to recover the .jpegs. I'll have to wait and see!
My main problems are, I think:-
1. Finding a way to put all the recovered .jpegs (which incidentally are a mixture perhaps 3:1 photos (hopefully with intact exif data),and other image files, into a folder perhaps 'Recovered Files' so that my /home/ray folder isn't cluttered and virtually unusable.
2.To sort out the photos from the other jpegs. This may be very simple using Shotwell which should put the photos into Year, Month and Day folders.

Would you be so kind as to tell me what commands I should use? Do you think it makes any difference if I install Shotwell before or after the sorting?

---

### Post by RayArdia on 2014-01-01
From the link you gave [http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec) this looks interesting:-

     JPEG file sorting using Exif meta-data.
    Canon PowerShot models store their image sequence numbers in the Exif data, so using a program that can dump Exif data to text like jhead, and the following Perl script, you can essentially restore all the JPG files to their original names. --Vees 01:59, 8 January 2007 (CET) 

My problem is that since I don't really understand the command's logic, I'm chary to use it.

---

### Post by oldfred on 2014-01-01
I do not use shotwell, but would expect it would spend a lot of time with that many pictures finding them. Then if you reorganize then it takes time to refind them.

You should be able to use Nautilus as a gui, or cp -a, or rsync as command line tools to copy files. 

This has a python app to sort and move files.
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

