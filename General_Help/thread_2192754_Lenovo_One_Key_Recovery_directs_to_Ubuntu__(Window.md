---
title: "Lenovo One Key Recovery directs to Ubuntu  (Windows 8 recovery partition is lost)"
date: 2013-12-09
forum: General Help
---

### Post by encinaar on 2013-12-09
I had many problems after installing Ubuntu 13.10. The first one was that the OS option menu was not vsibile (Only pruple screen was available) and I was not able to choose between Ubuntu, Ubuntu Recovery, Windows 8, ...etc. After many attempts to solve this problem, I reinstalled Ubuntu 13.10 on the same partition. However, Windows 8 option is not available on the menu right now. The most caothic thing is that, "One Key Recovery" button does nothing but directing to Ubuntu. How can I make the recovery button work as usual and get access to Windows 8?

---

### Post by oldfred on 2013-12-09
Unless you used manual install or Something Else, there is no install on same partition, but just a install on entire drive.

Post this from liveCD or your install.
sudo parted -l

---

### Post by encinaar on 2013-12-10
Erase disk and install Ubuntu was my choice of installation.

---

### Post by oldfred on 2013-12-10
That erases the disk which is everything including the recovery partition.

Did you make a backup of the recovery partition and/or a full backup of the Windows c: "drive" which is another partition on the disk?
If not you may be able to get a recovery DVD set from the vendor for a nominal charge. It is not a full Windows installer like you purchase, but just a image that restores drive or like the one key recovery does.
Otherwise you probably have to purchase another full copy of Windows.

If you have some data you did not have backed up and absolute want it back there are tools to scan drive. Only files not overwritten may be recoverable. You do not get file names, but do get extensions or file type.

       For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

