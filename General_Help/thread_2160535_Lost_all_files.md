---
title: "Lost all files"
date: 2013-07-07
forum: General Help
---

### Post by quirino77 on 2013-07-07
I have dual boot with windows 7 just to play games.
So i booted yesterday to play. When came back to Ubuntu, could not mount the partition anymore (not clean). But could not fix. When booted again on windows, it ran check disk on boot and "recovered" many things. And all my files where gone. ntfsundelete found nothing. getdataback almost nothing.

Any ideas?

---

### Post by ohnonot on 2013-07-09
try to boot from a live cd/usb.
can you still access the ubuntu partition?

---

### Post by quirino77 on 2013-07-09
Yes.
Actually, both OS (Ubuntu and Windows) are on a SSD. The HD is just for files and is NTFS.
I booted from SSD on Linux and tried ntfsundelete and got nothing, on windows and tried getdataback and got a few files.

---

### Post by quirino77 on 2013-07-09
I forgot. The partition have no errors. The only thing is that files were gone after windows check disk.
Should i remove the partition and run getdataback, or recreate the partition and run ntfsundelete?

---

### Post by dannyboy79 on 2013-07-09
what files were gone? you're missing files from Windows or you're missing files from Ubuntu?

It sounds like you're mounting your NTFS partition in linux and you couldn't because it wasn't shutdown properly and when you fired up windows, it ran check disk and possibly removed some of your files. If that was the case I am guessing they are gone IF windows check disk removed them.

---

### Post by ohnonot on 2013-07-09
i would not recommend running any windows tools that might affect your linux partitions.

to get things clear:
you have both windows and ubuntu installed on an ssd, and your data/files is on a (probably external) ntfs hard drive?
the files that are gone,  do you mean the ubuntu partition on the ssd or some data on your other hd or both?
can you boot ubuntu and/or windows normally?

please give as much info as possible and be precise about what you are asking help for.

---

### Post by Mark Phelps on 2013-07-09
Word of advice -- when you're having filesystem problems with NTFS partitions, NEVER run any Linux utilities against those partitions. Period.

GetDataBack is one of the best Windows data recovery apps available, but since you ran a Linux utility against the filesystem first, there's no telling how much additional damage that did.

---

### Post by tareqjhe1 on 2013-07-09
Which version you installed?

---

### Post by quirino77 on 2013-07-09
Thank's for all the suggestion.
I have on SSD with Windows 7 and Ubuntu 12.04, both 64 bits.
I also have a 1 TB HD, one partition (NTFS) with many files (thousands). Both Windows and Linux had access to it.
Everything was ok. So i went on Windows to install a game on Steam. The download would take long, and i used the shutdown -t 8000 on Windows to shutdown later and went to sleep.
On the other day, i started my PC on Ubuntu (the default) and Ubunt could not mount the media (NTFS HD). On disk utility it said "not clean". Since NTFS is native from Windows, i thought it would be better to let Windows handle it. On boot, Windows made a scan for error and "fixed" lots off errors. The verbose is fast, but i could see some folders and files names while Windows was "fixxing" the disk. I rebooted on Linux again and no files on disk. Came back to Windows and no files too.

Then i ran get data back (version 2.25) and very few files where recovered. So i tried ntfsundelete (it do not write on disk) and it could recover NO files.
Both OS are runnig fine. No problem on SSD.

---

### Post by ohnonot on 2013-07-09
+1 to mark phelps answer.
i'd just like to point out that it is not opposed to what i recommended earlier!

"Word of advice -- when you're having filesystem problems with NTFS partitions, NEVER run any Linux utilities against those partitions. "
and
"i would not recommend running any windows tools that might affect your linux partitions."
are not mutually exclusive.

---

### Post by quirino77 on 2013-07-10
Up!

---

### Post by ohnonot on 2013-07-11
> **quirino77 said:**
> Then i ran get data back (version 2.25) and very few files where recovered. So i tried ntfsundelete (it do not write on disk) and it could recover NO files.is this the "get data back" windows utility mark phelps was talking about?
and the other one, windows or linux?

i once managed to recover a LOT from an ext4 (=linux) filesystem with [photorec(overy)](http://www.cgsecurity.org/wiki/PhotoRec).

rant:
i have a 500GB usb external drive which was formatted ntfs from the factory, containing all my music, photos, videos...
after changing to linux i'd still use it but it was acting up strangely, i thought it's dying on me and in a long session i copied the stuff over to some other hd and reformatted it to ext4. since then the external hard drive is working again as if nothing happened.
i thought it was a problem if i can't access the drive with windows, but i just never ever boot into windows although i still have it on a spare laptop.
the few times i'm moving data between OS's, i put it on a memory stick (which is formatted fat32) and take it with me.

---

