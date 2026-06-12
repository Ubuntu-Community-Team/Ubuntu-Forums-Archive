---
title: "Gparted 0.25.0 (Xubuntu 16.04) won't shrink Windows Vista Partition"
date: 2017-01-08
forum: General Help
---

### Post by Ralph L on 2017-01-08
I am trying to shrink the Vista partition on my dual boot disk.  I booted from a flash drive with the Xubuntu 16.04 OS straight from the download.  When I right-click on the ntfs partition I can select Resize/Move, but when that window comes up I can't shrink the partition and the Resize/Move button/box at the bottom right is grayed out.  There is a warning sign on the Vista partition with the message:  ```
Unable to read the contents of this file sytem!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs files system support:  ntfsprogs / ntfs-3g

``` I have ntfs-3g installed.  I don't have ntfsprogs installed, but I understand that it has been combined with ntfs-3g.  I found that if I booted from an old CD with Ubuntu 12.04 on it, and an older version of Gparted, that I could set up the shrink, but I want to use the latest version of Gparted in case it handles Vista partitions better.  Can anybody tell me how to shrink my Vista ntfs partition???

---

### Post by Irihapeti on 2017-01-08
There is apparently a bug in the 16.04 version of Gparted, which might explain what you're seeing.

However, it's generally recommended to use Windows tools for Windows partitions. It's a long time since I used Vista, but I seem to recall that it has a partitioning utility.

---

### Post by gedakc on 2017-01-09
If you wish to use the latest version of the GParted application, download the most recent [GParted Live]("http://gparted.org/livecd.php") image, write it to CD/DVD or USB flash media, and then boot from this media.  That way you will have the latest version of GParted straight from the project web site.

---

### Post by efflandt on 2017-01-10
Win 7 has its own "Disk Management" to shrink its partition, but not sure about Vista. I know that Win XP could not shrink itself and you had to disable virtual memory (Windows version of swap file) before shrinking it with Linux. That was because it usually put the virtual memory file at the far end of the drive and that file was not movable with defrag. Hence you had to temporarily disable virtual memory before/while shrinking.

---

### Post by Ralph L on 2017-01-10
Thank you very much to those who responded to me on this issue.  You helped point me in the right direction.  Yes, in Window Vista I disabled both hibernation and virtual memory so that those files didn't need to be moved.  I deleted both the hibernation file and the pagefile file.  There are a number of web sites that tell how to do that.  

It turns out that the message that gparted issues when I clicked on the yellow triangular warning icon is very misleading.  In my case the problem had nothing to do with the warning message that said that ntfsprogs and ntfs-3g might need to be downloaded.  First, ntfsprogs has been incorporated into ntfs-3g, so it doesn't even exist in newer systems.  Second, ntfs-3g was installed in the xubuntu release live flash drive.  As a side note I couldn't get the program "Software" to work on the Xubuntu 16.04 live flash drive.  I had to boot up a live flash drive of Lubuntu 16.04 that had Synaptic in it to discover that ntfs-3g was already installed.  No idea of what was wrong with "Software".  Anyway, it appears that gparted sets the yellow warning symbol whenever it finds something not right in a partition.  Once I found that, I booted Vista and forced it to do "chkdsk" on the Vista partition during the next boot.  (There are numerous web sites that tell how to do this.) Also, with multiple bootable disk partitions on the system, I had to select the Vista partition after each chkdsk to get it boot correctly)  "chkdsk" repaired the Vista partition and then gparted was perfectly happy and moved it fine.  When I restarted Vista after the move it automatically did a chkdsk during boot and then booted with no problem.  In fact, I resized the Vista partition 2 or 3 times, and each time it automatically did a chkdsk, when I subsequently booted Vista.  One thing I forgot to mention is that before attempting shrinking the Vista partition with gparted, I defraged the Vista disk with JkDefragPortable--free version (after deleting the hibernation and pagefile).  I set it to "defrag and optimize", and it sure ran a long time, but seemed to really pack the files down so that shrinking the partition would be easier.

Hope this helps somebody!!

---

