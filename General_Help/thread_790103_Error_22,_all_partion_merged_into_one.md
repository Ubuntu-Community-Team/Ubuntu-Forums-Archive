---
title: "Error 22, all partion merged into one"
date: 2008-05-11
forum: General Help
---

### Post by vetinte on 2008-05-11
Hi, I hate the thought about Microsoft is the leading OS, so I started to learnt Ubuntu.
I’m totally noob in it.

My problem is this, I have an hdd 250Gb I split it like this:
1.	Partion is Win XP (NTFS)
2.	Partion is storage (program) (NTFS)
3.	Partion is storage (NTFS)
4.	Partion is Root Ubuntu (ect3)
5.	Partion is Swap ubuntu
6.	Partion is storage (FAT32)
7.	Backup storage

Partion 1, 2, 3 is created with Win XP
Partion 4, 5, 6 is created with Ubuntu
Partion 7 is created with bios backup

The problem was that I tried to change partion 6 from Fat32 to ect3 in gparted, that was easy, so I thought that it was wrong, so I went to “Device – set disklable..” but all partion merged to one, so now I have only one partion and a grub error 22.
I know that I have not lost everything, but how do I fix this with out losing everything or not losing partion 1, 2 and 3.

Any ides?

---

### Post by ASULutzy on 2008-05-11
How are you testing to see that there's only one partition now instead of the 7 that were there before?

---

### Post by ryanhaigh on 2008-05-11
Assuming that you have indeed deleted your partition information you may want to try using testdisk to recover the information. You can using your existing livecd and when its running install testdisk by enabling universe in system>admin>software sources  and then ```
sudo apt-get install testdisk
```.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

