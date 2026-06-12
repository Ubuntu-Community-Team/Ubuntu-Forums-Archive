---
title: "SOS for folder recovery, about 800 GB at stake! Help please."
date: 2013-03-09
forum: General Help
---

### Post by cpyder on 2013-03-09
Hello there,

I join elite group where people have lost the data - with a few twists.

I was trying to clone Windows 8 partition from HD1 to HD2 using clonezilla.  The target drive HD2 had two partitions. The windos 8 partition was successfully cloned, and then I noticed that it started cloning second partition of source HD1 into second partition of target HD2. I aborted the process but the damage had been done. some 7 GB of data had been already written into the target HD2/ partition 2.

I need to recover stuff from second partition of target HD2. It is 830 GB partition which has all my photographs, home videos, movie collections and music. Data is close to 790 GB.

I used photorec and scalpel, but these programs are recovering stuff with no names or directory structure.  Every thing is dumped in few directories.  Thats huge headache to sort out when I talk of 790 GB worth of files!

So, is there something that can help recover files with some semblance of original directory structure? Is there something that can be done here??  Its a huge huge digital loss staring at me.

---

### Post by black veils on 2013-03-09
you can try testdisk to recover the partition instead of individual files.

---

### Post by Cheesemill on 2013-03-09
> **cpyder said:**
> I used photorec and scalpel, but these programs are recovering stuff with no names or directory structure.  Every thing is dumped in few directories.  Thats huge headache to sort out when I talk of 790 GB worth of files!

I think that is the best you are going to get.

Filenames and directory structure are stored in the FAT (File Allocation Table) which lives at the start of the partition.

Once you have overwritten the first few MB's of a partition that contains all of the allocation table then the names and directory structure are lost. The easiest way to get everything back is to restore the data from your last backup.

If any of it is mp3 files then you may be able to use a tag editor to restore the filenames, as the ID3 tags are part of the actual file.

---

### Post by Vaphell on 2013-03-09
you can also go to people who do data recovery for a living but i guess it's quite expensive.

And if the collection is priceless, why on earth you don't have a backup or two? You never experienced an old fashioned HDD failure?

---

### Post by cpyder on 2013-03-10
> **Cheesemill said:**
> I think that is the best you are going to get.

Filenames and directory structure are stored in the FAT (File Allocation Table) which lives at the start of the partition.

Once you have overwritten the first few MB's of a partition that contains all of the allocation table then the names and directory structure are lost. The easiest way to get everything back is to restore the data from your last backup.

If any of it is mp3 files then you may be able to use a tag editor to restore the filenames, as the ID3 tags are part of the actual file.

OK, So I guess that pretty much seals my fate. Phew.. But I will still wait .. hope to find a better way.  The idea of M ID3 tags is, good will try.  And that makes me think, the photographs' EXIF data can at least help in chronological sorting. Thanks Cheesemill.

> **Vaphell said:**
> you can also go to people who do data recovery for a living but i guess it's quite expensive.

And if the collection is priceless, why on earth you don't have a backup or two? You never experienced an old fashioned HDD failure?

Yeah.. un(?)fortunately nope! In last decade and a half of my active computing life, never had a disaster like this. So now I believe in the saying - its not 'IF' you lose your data, but 'WHEN' you lose your data. Read it yesterday itself.

So now I am gonna get another drive and read up on carving and all.

OK Guys, can someone help me out with easing my agony just a little bit.  Although I did try photorec and scalpel, I am by no means a geek.  Is there a way to recover files meeting certain criteria like size, file extension etc.  And how do we do it?
How can use the exif data so that photographs taken from a particular camera are sorted into one directory?

-Ideas?? anyone?

Thanks guys

---

### Post by oldfred on 2013-03-10
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

I recovered a lot of text & python files. After manually sorting and comparing/searching files with grep I went back and added file name to the start of every text or file that I can edit manually. I found photorec not only found my files, but it found all the backups or older versions. And some of the files I had saved many times since my last real backup. Never was sure I found last saved version. I had created my own little script to sort files before I found photorec already had that.

---

