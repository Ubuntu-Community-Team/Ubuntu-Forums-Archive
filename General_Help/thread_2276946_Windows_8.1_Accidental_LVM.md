---
title: "Windows 8.1 Accidental LVM"
date: 2015-05-05
forum: General Help
---

### Post by c.shinx on 2015-05-05
So, the title pretty much says it all, but here's the gist of what happened: 

I was trying to install Ubuntu (14.04.2 LTS) and I got to the install page that asks if you want to erase what is on the disk, or do somehing else.
I made the terrible mistake of thinking LVM was a different option than erase disk. After I clicked on it, I had realized what I had done and began spamming the "esc" key as fast as I could. Another window popped up, but I accidently closed out of it with my "esc" key pressing. Whatever I did, it seemed to have stopped the erasing, but after quiting the install, I was unable to boot back to Windows. Is all of my data irreversably damaged or am I still able to get back some of my personal files? It won't be the end of the world if I have to reinstall Windows, but I am more worried about being able to get back my personal documents. 

Any help would be appreciated, thanks!

---

### Post by oldfred on 2015-05-05
It depends a lot on how much was written.

You can use testdisk and see if it finds old partitions. If it shows files then your are lucky.
Part of testdisk is photorec which scans a drive for anything that looks like a file by type. But not full file name. You need lots of space or another drive for it to copy data to.

Both testdisk & photorec are in repository.
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

        [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

If NTFS then Windows tools may work better.
      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

