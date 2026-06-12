---
title: "Disk Recovery Software"
date: 2018-09-23
forum: General Help
---

### Post by shag00 on 2018-09-23
I installed 18.04.01 and as part of the process it appears to have corrupted the partition tables of 2 HDD I had in the system. I thought to myself that's no problem and so I re-partitioned them knowing I would loose all the data. Ah yes, a couple of days later I remembered I needed some of the data..... Fortunately, apart from the new partition table created during the format the HDDs have not been written to.

I have a system drive in addition to the 2 HDD but it is only 250GB while the HDDs are 2TB each. I installed Testdisk but the problem is the mismatch in disk sizes, it always stops when it runs out of spare space on the system disk. So Testdisk is finding and copying files.

So what i am after is a disk recovery program that first generates a list of recoverable files and then gives me the option to copy/restore/save the files I want. Of the 2TB capacity maybe 1 Tb was used and of that I probably need about 2 dozen files or less than 2 GB.

---

### Post by ajgreeny on 2018-09-23
Have a look at [Testdisk]("https://www.cgsecurity.org/wiki/TestDisk") which may be able to restore your previous partitions.

I have never used it, and so far, thank goodness, never needed to, but it is often recommended in these forums.

---

### Post by dragonfly41 on 2018-09-23
> [COLOR=#000000]Ah yes, a couple of days later I remembered I needed some of the data..... Fortunately, apart from the new partition table created during the format the HDDs have not been written to.[/COLOR]

It is not clear to me whether your lost data is across these two HHD's or within just one of them? Do you know for sure which one?

Assuming that you don't intend buying a new 2 TB drive, can you safely use one of the 2 TB drives to receive testdisk recovered files? However a third 2 TB drive could prove useful for backup purposes for such events.

It is some time since I last used testdisk but there is an option to hide previously deleted files which I presume you do not want to include in recovery? Testdisk needs a repository for recovered files as large as the disk drive being scanned.

This post reminds me that I must backup my partition data on an external flash drive.

---

### Post by shag00 on 2018-09-23
@ajgreeny, I think I mentioned it in the OP.

@dragonfly41 The data I want is just 1 directory on just 1 HDD but with new volume labels etc I have no idea which disk. Both drives in question are backup drives which is why I did not mind to lose the data on them with 1 of them partitioned for non backup use. The non backup partition has data I was using to test wine to see if I can ditch Windows 10 altogether. 

Yes there is that option to hide files but I do not know how to invoke it without all files having previously been copied to a new disk, Testdisk also renames everything recoveredfile1, recoveredfile2 etc but are actually directories. So that is why I was after a program that report the old file structure and then allow me to select what files I want to recover.

---

### Post by dragonfly41 on 2018-09-24
I thought that only photorec remamed files in that manner.

I would try [R-Linux]("http://www.r-tt.com") which runs on Ubuntu.

---

### Post by shag00 on 2018-09-24
dragonfly, seems i will just need to rebuild the data but thanks for your time. I was hoping for something that displayed a file structure that was human readable but it has a similar naming convention to Testdisk.

---

