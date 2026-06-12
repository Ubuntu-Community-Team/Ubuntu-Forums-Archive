---
title: "Partition empty after ntfsresize. How to recover ?"
date: 2013-02-15
forum: General Help
---

### Post by java.artisan on 2013-02-15
I was trying to shrink the windows partition on sda3 to install Ubuntu. Apparently it has bad sectors. Which is a problem apparently for the installer. So...

I did the following:

(1) ntfsresize -b -s 250000M /dev/sda3
(2) removed the partition in GParted
(3) recreated the partition with the right size

==> The partition is empty. Meaning no files anymore. 

I guess I did something horribly wrong here... :-(


Is there any way to recover the partition still ?

---

### Post by oldfred on 2013-02-15
Always shrink Windows from inside Windows (unless XP) and reboot as it has to run chkdsk. Windows PBR or partition boot sector has to have same information as partition table on start & size of NTFS partition.

You might try testdisk.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

    
       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by java.artisan on 2013-02-15
I'll try testdisk - thanks !

But it is possible to recover from the creation of a partition with gparted ? If I'm not mistaken it does mkfs.ntfs /dev/sda3. Isn't that fatal ?

---

### Post by oldfred on 2013-02-15
Not sure. Formatting may write some files structures, but whether they conflict or overwrite I do not know.

If deep search with Testdisk does not work, then you can use photorec. But it is a long slow process. And you have to have another drive with room for everything it finds. It just scans drive for anything that looks like a file by type, but cannot restore file names, just extensions. And it recovers deleted files as I had many versions of the same file recovered and never was able to figure out which was most recent. I has to do a lot of comparisons.

---

