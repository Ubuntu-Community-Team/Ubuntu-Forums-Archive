---
title: "Gutsy won't copy a 4.1 GiB iso to another HDD. Help?"
date: 2008-03-16
forum: General Help
---

### Post by JimmyHopkins on 2008-03-16
I should mention I'm running Gutsy on an i386 (P4) with all updates available installed.
I have 9 iso's in my home folder (which is on sda7, while ubuntu is on sda5). I try to copy the 9 .iso's to an external HDD (500 GiB, with 150 GiB available). Each iso is almost exactly 4 GiB. Anyway, during some iso's (such as one that is 4.1 GiB), ubuntu stops copying, and closes every windows down (ie /home, /media/my external HDD) and brings up my /home. Then I tried copying each .ISO individually, no luck. Any help please?

Cliffnotes:
9 iso's, 4 GiB each
Try to copy from /home to /media/my external HDD
No luck
I try copying each iso by itself
No luck

Thanks in advance.

EDIT: Oh yea, my external HDD is fat32 and other files copy and play off of it quite nicely.

---

### Post by Rocket2DMn on 2008-03-16
FAT32 doesn't support file sizes over 4GB (2^32=4,294,967,296 bytes to be exact).  Anything that exceeds that cannot be written to the FAT32 partition.  The drive will need to be formatted with another file system like NTFS or ext3 (the default in linux).

---

### Post by JimmyHopkins on 2008-03-16
Wow, I'm such an idiot. I told you it was fat32 because I thought maybe linux couldn't write to fat32 well (I don't know why I thought this, linux has been writing to fat32 for years, it's NTFS that used to be a problem.)

Thanks for your help. I looked up ext3 files sizes last night, it's something like 16GiB I believe. Unfortunately, I need this external HDD for windows, so ext3 is out of the question. Looks like I'll try NTFS, but since I only have a 120 GiB HDD, and I have 400 GiB of date on my external HDD, it looks like I've have to wait 'till I get another HDD. I've heard of the 4GiB limit, but I thought that was fat, since fat32 is still used, I thought fat32 couldn't be that limiting. I guess I was wrong.

Thanks again.

---

### Post by PeterJS on 2008-03-16
Not to dissuade of from using NTFS but there are ext2/3 drivers for windows, you can grab them here:
[http://fs-driver.org](http://fs-driver.org)

---

