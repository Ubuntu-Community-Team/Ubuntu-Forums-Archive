---
title: "Query re. NFS, fstab &amp; also Auto Mounter"
date: 2007-08-04
forum: General Help
---

### Post by idheath on 2007-08-04
Hi,

I have some queries with regard to using NFS between my Ubuntu server & workstation.

I have 3 directories that I have shared via NFS on my server as follows:

/export/data1-raid
/export/data2
/export/data3

'exports' contains

/export/data1-raid 172.16.1.0/255.255.255.0(rw,sync)
/export/data2 172.16.1.0/255.255.255.0(rw,sync)
/export/data3 172.16.1.0/255.255.255.0(rw,sync)

On the client I added the following 3 lines to my fstab

172.16.1.123:/export/data1-raid /mnt/data1-raid nfs rw,hard,intr 0       0
172.16.1.123:/export/data2       /mnt/data2      nfs     rw,hard,intr    0      0
172.16.1.123:/export/data3       /mnt/data3      nfs     rw,hard,intr    0      0

And after a 'mount -a' everything was fine.

I few days later I checked them and only the /mnt/data1-raid mount was available on the workstation.  I checked with 'mount' and non of the 3 entries were there (not even the /mnt/data1-raid on which was mounted!).

Next I checked fstab and it only had the 1st of the above entries there (and unless I'm going mad, I didn't remove the others from ftsab).  Does anything modify fstab?

Anyway I re-added the missing 2 lines to fstab and did a 'mount -a' and although I got an error saying /mnt/data1-raid was already mounted the other 2 mounted OK.

When I did a 'mount' again I can only see the last 2 entries (/mnt/data2 & /mnt/data3) but all 3 mounts are available.

Any thoughts would be appreciated.

Regards Ian

---

### Post by idheath on 2007-08-04
Ignore the reference to Auto Mounter in the post title (I was going to add some questions about that too but I'll post that query separately).

---

