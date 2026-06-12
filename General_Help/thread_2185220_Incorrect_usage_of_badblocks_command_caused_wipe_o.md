---
title: "Incorrect usage of badblocks command caused wipe of all data on 1TB portable drive"
date: 2013-11-01
forum: General Help
---

### Post by khq_rpc on 2013-11-01
Hello, 
Using Ubuntu 12.04 with xfce disktop manager 

:(unfortunately while I tried to use badblocks command from Terminal to check if my 1TB portable drive is affected during long trip 
my mistake that I used the command with the wrong switch -w (badblocks - w /dev/sdb1) !!!!!!!!!!!!!!!!!!!!!
I found that my drive is appearing as (unknown) in disk utility I thought maybe partition table was damaged , so I searched every where for a utility to rebuild my corrupted partition table and giving me access to my 290GB of data in this drive , at this moment I found everyone saying the testdisk is the one for that job ...
result of using testdisk is an old partition with non related data , and it didn't recognize any of clue about the fresh missing partition 
now I stopped in order not to over write any more data on the drive until I find powerful utility to search the disk media surface for files and reconstruct the missing partition table 
just to make sure, I used Recuva file recovery utility to search the drive and it successfully found my files without names or any other properties (just numirci names and correct file extension) ...

:(The point here that I am unable to find a big storage to recover all my files in it from this drive, additionally I can't rename 307070 file after recovery !!!!

what I need is a mean to reconstruct my lost partition table to access all my files which is not over written yet in this media till now , and waiting to be accessed !!! just reconstruct the partition table probably ...

Any one can help with an advise about this catastrophic problem ....  

thanks all for your time reading this 

best  wishes (and honest prayers to all not to be in this situation ever :p) 

Khaled:KS

---

### Post by SeijiSensei on 2013-11-01
Try fdisk or parted from the command prompt; gparted for a GUI.

---

### Post by tgalati4 on 2013-11-01
If *testdisk* was not able to reconstruct the partition, then your only recourse is to use *photorec* (which is part of testdisk) to simply recover files with useless names.  All 300 thousand of them.

I have not used *badblocks* with the -w switch in a long time.  Wasn't there a warning in large capital letters saying that this would destroy all data on this disk?

---

### Post by khq_rpc on 2013-11-01
Thanks SeijiSensei for your reply 
fdisk , parted, gparted and other tools (testdisk, Partition Find and Mount, Disk Digger, Partition Recovery) all fail to reconstruct the damaged partition table :mad:

Do you have another idea ?

---

### Post by khq_rpc on 2013-11-01
> **tgalati4 said:**
> If *testdisk* was not able to reconstruct the partition, then your only recourse is to use *photorec* (which is part of testdisk) to simply recover files with useless names.  All 300 thousand of them.

I have not used *badblocks* with the -w switch in a long time.  Wasn't there a warning in large capital letters saying that this would destroy all data on this disk?

@tgalati4 : actually this is exactly what I am trying hardly to avoid , for 2 reasons: - 
1- the amount of data is bigger than any storage I do have write now to use to recover files in it 
2- the useless names means useless files !!!

I would appreciate any other idea about rebuilding the lost partition 

thanks

---

### Post by tgalati4 on 2013-11-01
It sounds like *badblocks* overwrote critical portions of the partition table and backups of the inode data which is needed to create a file structure.  That is why all of the standard tools failed--they all rely on this backup data to recreate a functioning partition and file structure.  Even a partial reconstruction would help, but that does not appear to be the case.

So your recourse now is:

1.  Go out and purchase an external drive that is bigger than your recovery needs.
2.  Start research on scripts to rename files based on ID3 tags, EXIF data, etc.

Group your files based on type:  Music, Videos, Photos, documents, etc.  Search for specific naming scripts for each type.  It's tedious, but the alternative is to not have useful file names.

You really don't need to rename the files because most applications have built-in indexers.  For instance, if you import your entire directory of nameless music files into Rhythmbox, it will create an index based on ID3 tags and you can quickly find tracks that you want to hear.  *easytag* can also be used to rename files based on ID3 tags.  gthumb or F-spot can handle photos by laying them out with thumbnails and then you can group them visually or search by EXIF data.  Videos can also be handled by another media player for indexing.  It's documents and random data that you will have trouble sorting out.

There are many tools and operations that will quickly and completely destroy a partition.  You have found one of them.

---

### Post by khq_rpc on 2013-11-14
Just to share info with my friends here ... :popcorn:
After endless continues hours of trials of all program I could reach, I found one program called (Partition Guru) which was able to reconstruct the partition table during file recovery process for my external HDD  .... it started with surface scan of the hard disk , and based on good logic (by using any file data it encounter, along with any remnant partition / boot sectors during the scan) it was able to offer me all possibilities of partition structure including old deleted partitions , and of course my lost partition was on top of them without missing any info ... 

The concept behind the success of this utility was clear ... using every thing it find with full scan and not only depend on backups / old / remnant partition / boot sectors ... :)
in comparison to famous TestDeisk utility , Partition Guru was doing the job right ... TestDisk depends on those left behind sectors to reconstruct the partition table structure , regardless to the surface scan it do the the HDD ... someone need to talk to the developers to rethink about it again 

:idea: the missing trick yet, is although that Partition Guru was able to reconstruct the partition table and its contents of file system correctly , it didn't offer to write these findings to the same media , but instead offer it as a virtual disk to use for recovering files from the missing partition to another media .... 

BTW: one of utilities I used at first was GetData Back NTFS which was my favorite since long time , and I was shocked that it didn't recognize my lost partition at all , and didn't list it between history list of old partitions found in that drive ... although that specific partition was not altered at all since damaged !!! :(

any way I hope if someone here know about any utility that reconstruct the partition table using surface scan by the same technique I mentioned here (which is BTW is used in many professional file recovery utilities) , to help me restore access to my partition as it is without the need to recover all of my files first to another drive (found that they area 667GB of video data !!! :shock:) ... as long as the concept is easy ( as in this example) so for sure someone did make some utility for us in Linux community to get this function working with us also (reconstructing Partition table and file system from surface scan of storage media)

waiting your feedback my dear Linux / Ubuntu Geeks :KS

@:[COLOR=#000000][[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895") [/COLOR]
[COLOR=#000000][/COLOR]: I apretiate your help, but my advise to you never pick up the easy solution if it will mean to rebuild all your work, specially if you don't reach to the root cause of problem at first hand ... your stratigy is much more lasy and involve rebuilding the whole liberary , without touching the core of the problem , which is technically possible to be solved ... all what is required is some digging for information and to check around my be someone else did solve it before :) ... thanls again and keep up ;)

Khaled

---

