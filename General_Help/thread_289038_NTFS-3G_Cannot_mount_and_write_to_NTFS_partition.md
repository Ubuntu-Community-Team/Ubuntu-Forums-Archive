---
title: "NTFS-3G Cannot mount and write to NTFS partition"
date: 2006-10-30
forum: General Help
---

### Post by divas on 2006-10-30
Hi,

I have two ntfs partitions mounted to /media/win1 and /media/win2 respectively.
Note: I can mount those partitions but I cannot write in them.
So I installed ntfs-3g. I followed all the instructions given in
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
but no luck.
I think the problem is with fstab.
I added those two lines:
/dev/hdb1 /media/win1 ntfs-3g     defaults,locale=en_US.utf8   0    0
/dev/hdb5 /media/win2 ntfs-3g     defaults,locale=en_US.utf8   0    0

According to another thread, I've added "sudo" in my /etc/modules file.
When I restart the computer the partitions are not mounted any more. When I click on a partition it says: "Cannot mount the partition, there is a problem in your fstab file in lines 8 and 9."

According to another thread, I've added "sudo" in my /etc/modules file but still no luck.

I 've been working two days in this problem and no luck.
I 'm new to linux and any help would be greatly appreciated.
Thanks in advance!

---

### Post by em es on 2006-10-30
I mounted my Windows partition yesterday, and I didn't have to alter the modules file. Are you on edgy? Because if you are you've got a UUID file.

If that is the case then just rename the "fstab.pre_uuid" file to fstab and alter it in there.

---

### Post by divas on 2006-10-30
Thanks man but, finally, I found the solution.
The problem was not with the mounting procedure. It was with the f..cking Nautilus (or whatever the name of the linux-explorer is).
After A LOT of experiment I realised that I can browse my NTFS partitions through a terminal and I can write files on them. But when I go to Places-> Computer, and click on one of the drives, it says: "according to mtab /dev/hdb1 is already mounted on /media/win1".
What I did was to create a soft link in my desktop to /media/win1 and /media/win2.
and YES!!!
For those who say that ntfs-3g can only mount one partition, I inform you that I CAN WRITE TO BOTH OF MY NTFS PARTITIONS!!!!

Anyway, thanks for the reply man!

---

