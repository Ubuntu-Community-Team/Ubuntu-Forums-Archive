---
title: "Recover GPT (to recover my files), External USB HD with HFS+ File System."
date: 2017-09-13
forum: General Help
---

### Post by joseluisbz on 2017-09-13
Hi, My Hard Disk was corrupted by accidental disconnection from my MacBook Air, I was using Virtual Machine performing search Windows 10.

Now, I can't recover my personal files.

[HTML]ubuntu@ubuntu:~$ sudo parted /dev/sdd
Warning: Error fsyncing/closing /dev/sdd1: Input/output error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdd2: Input/output error
Retry/Ignore? R
Warning: Error fsyncing/closing /dev/sdd2: Input/output error
Retry/Ignore?                                                             
Retry/Ignore? ^C                                                          
Warning: Error fsyncing/closing /dev/sdd: Input/output error
Retry/Ignore? c
parted: invalid token: c
Retry/Ignore? ^C  [/HTML]


I post question on [https://askubuntu.com/questions/955325/using-gpart-testdisk-to-recover-gpt-for-files-from-damaged-hfs-apple-hd](https://askubuntu.com/questions/955325/using-gpart-testdisk-to-recover-gpt-for-files-from-damaged-hfs-apple-hd)


The last screen using **testdisk** is

[HTML]TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdd - 1000 GB / 931 GiB - CHS 953869 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors

Trying alternate GPT












                P=Primary  D=Deleted
>[Quick Search]
                            Try to locate partition[/HTML]

---

### Post by oldfred on 2017-09-13
Have you tried gdisk?

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/
[/URL][http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 

 sudo gdisk /dev/sdd
Command (? for help):

---

### Post by joseluisbz on 2017-09-14
Here result of **gdisk**
[HTML]
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 1.0.1

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdd: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 316B429D-ABB4-4BD3-80A2-CA0878DEDC3E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1953525101 sectors (931.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 1.0.1

Problem reading disk in BasicMBRData::ReadMBRData()!
Warning! Read error 22; strange behavior now likely!
Warning! Read error 22; strange behavior now likely!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdd: 0 sectors, 0 bytes
Logical sector size: 512 bytes
Disk identifier (GUID): 34FFA41B-68D0-4A3C-A6DC-91C51530DE76
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 18446744073709551582
Partitions will be aligned on 2048-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
ubuntu@ubuntu:~$ 
[/HTML]
The result of **fdisk -lu**
[HTML]
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sdd
fdisk: cannot open /dev/sdd: Input/output error
ubuntu@ubuntu:~$
[/HTML]

---

### Post by oldfred on 2017-09-14
Highly unusual, normally even if primary gpt partition table is damaged, then backup is ok or usable.
Its as if you erased entire drive?

If testdisk does not show anything, then best option is to reformat/repartition drive and restore from your backups.
I have used photorec.
But it takes forever, has to have another drive large enough to store recovered data, and recovered data is by name extension or type, not full file name. I went back and on all my text files added the file name as first line as it was only text files I wanted to recover. Photorec also found all the old copies as I had saved some files multiple times. Not sure then which copy was most recent. Lots of grepping & comparing to last backup and the multiple copies found. 

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

