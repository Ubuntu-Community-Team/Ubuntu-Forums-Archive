---
title: "How to reclaim used space in SSD (1 partition)?"
date: 2017-01-25
forum: General Help
---

### Post by javierdl on 2017-01-25
I just erased all partitions I had before, and formatted them to ext4, and although it is now just one big partition in my 128Gb SSD, Gparted shows that there's 1.94Gb "used".
I understand that some space will have to remain usable only for the drive, but that much?!  How erase what ever that is then?

Thanks guys :)

JDL

---

### Post by HermanAB on 2017-01-25
It is the journal.

---

### Post by oldfred on 2017-01-26
And the reserved space which you can adjust. (journal & format you cannot adjust).

 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sda1
also shows settings of mount count & how often it will run fsck on reboots 
man tune2fs

Separately I have seen that you should have unused space on SSD, so SSD can managed itself. Not sure if that is better outside a partition or ok inside a partition.

---

### Post by javierdl on 2017-01-27
Thank you oldfred.
I thought I could use that space, but it seems is better to leave it alone.

Thanks HAB

---

