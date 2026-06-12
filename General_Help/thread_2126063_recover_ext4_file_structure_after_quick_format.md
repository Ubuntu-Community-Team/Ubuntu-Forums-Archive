---
title: "recover ext4 file structure after quick format"
date: 2013-03-15
forum: General Help
---

### Post by adlin5000 on 2013-03-15
I was installing a new hardrive and formatted the wrong 2TB drive. It was originally all ext4 and I deleted that partition and formated 1.9TB ext4 and the last GB Swap. Nothing has been written to either partition.

Is it possible to recover the folder structure or at least the file names? PhotoRec started to recover files but that won't work. I need at least the file names, preferably the folder structure .

If this has been answered, sorry. Please point me in the direction of the answer.

Thanks

---

### Post by tgalati4 on 2013-03-15
*Testdisk* can sometimes recover the partition and directory structure.  *Photorec* will recover individual files if testdisk doesn't work.  Filenames will be random, but at least you have the data.

```
sudo apt-get install testdisk
man testdisk
man photorec
```

---

### Post by adlin5000 on 2013-03-16
I tried testdisk but it would only find the new partition. Is there a how to for it? I could only find ones for ntfs. As for photorec, with probably somewhere in the couple of hundred thousands of files, without at least the file names that is not an option.

---

### Post by tgalati4 on 2013-03-16
Testdisk runs the same way under linux or windows.  Basically it tries to resurrect the file/directory structure using several methods.  If that doesn't work, and if photorec recovery is not acceptable, then your only recourse is to send the drive out to a recovery service, where they try to assemble the data by hand--and it's pricey.

For music files, the title and artist is usually in the id3 tag and there are several tools that can rename those files.  I would perform a complete photorec recovery regardless, before attempting other recovery methods. 

The manual page for testdisk is complete.  You could use the /dump switch to examine the raw data and see if you can recognize file and directory structures--stuff that didn't get overwritten.  Afterall, humans are still pretty good at pattern recognition.   In a photorec recovery, you will get thumbnail images with names embedded in them.  Then all you have to do is match the thumbnail with the actual image and rename it--again a pattern-recognition task that we are ideally suited for.

---

### Post by oldfred on 2013-03-16
It really is the same for Linux formated. Example with ext2, but again the same.

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)

Other Similar tools:
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Since 2TB is on the edge of MBR, was drive formated with MBR(msdos) partitioning or gpt partitioning. That is one of the first questions testdisk asks and it is important to know.

---

### Post by adlin5000 on 2013-03-16
tgalati4: Sorry but they don't really give a lot of info on those manual pages.

oldfred: thats one of the questions that they never really answered on their wiki. I believe it was MBR (thats the default with parted magic I think). Which option would that fall under?

I tried some experimenting with testdisk. Selecting none for partition type seemed to get the most results, and one that I think may be it, but it says damaged when I try to look at the files. It was the only ext4 result that said 2TB not 1.9TB. The other two Look like the partition with the 1GB swap taken out. (I took out all the non ext4 results)

```
>P ext4                     0   0  1 243201  80 63 3907029168 [2.0 TB Hard Disk]
 P ext4                     0  32 31 243073 210 15 3904978944
 P ext4                     0  32 33 243073 210 17 3904978944
```

These look promising but they "can't be recovered"

```
   ext4                 121420  22 59 364621 103 58 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  26  7 364621 107  6 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  29 18 364621 110 17 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  33 22 364621 114 21 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  36 17 364621 117 16 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  38 59 364621 119 58 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  41 38 364621 122 37 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  44 49 364621 125 48 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  48  5 364621 129  4 3907029168 [2.0 TB Hard Disk]
   ext4                 121420  50 63 364621 131 62 3907029168 [2.0 TB Hard Disk]
```

I am trying gpart now. Will see if that comes up with anything.

---

### Post by adlin5000 on 2013-03-16
Well looks like gpart was a bust.

```
Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```

I'm assuming all the zeros means it did not find anything.

Its looking like its a bust. Unless anyone has any more ideas or can tell me how to get the one partition that testdisk says is damaged back, I'll call it a loss.

---

### Post by oldfred on 2013-03-17
Then you are down to photorec.

 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by adlin5000 on 2013-03-17
I used photorec to recover the music files as I can use easytag to rename them from the tags. The rest is going to be a loss. It's not feasible to to through the massive amount of files to try and figure out what they are. (I'm not to go through 5 seasons of a tv show to try and figure out what episode each one is for example. and thats assuming I sort that particular series out of all the stuff.)

Thanks for help.

Thread marked as solved, sort of.

---

