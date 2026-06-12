---
title: "How to rescue 1 terabybe of files"
date: 2020-10-31
forum: General Help
---

### Post by handrew on 2020-10-31
Oh boy! I was formatting a USB stick but picked my storage hard disk by mistake and wrote a new FAT32 partition table over my EXT4 table. I have no knowledge how to rescue all my files, I assume it was just the table that was lost. Is there a way to save all my files are recreate a new table? I am in real trouble with my wife now!!! 

Anyone, thanks for helping!!!

---

### Post by Impavidus on 2020-10-31
Read about lost partition here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Chances are pretty good that you can recover (almost) all of it.

What was your plan in case your harddrive was really broken? It happens. There's no substitute for backups of your vital files.

---

### Post by oldfred on 2020-10-31
Have you rebooted?
There may be a way to revert if you have not rebooted.
MBR(msdos) or gpt?

Testdisk is usually one of the first choices as it finds old partition tables. If partitioned multiple times it finds all the versions and you have to select the correct combination.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You really do not want to have to use Photorec which is part of testdisk. It scans drive for anything that looks like a file, by type, but not full file name.
Takes a very long time, you need another drive that is same size as data you want to recover, and renaming files is a huge hassle. I have done it. It was only a few text files, had old backup, but many copies saved & it found all the copies. Lots of comparing and never knew if I restored all the data or not.

If not rebooted, use fdisk to manually recreate table posts by srs5694 post34 on page#4:
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

---

