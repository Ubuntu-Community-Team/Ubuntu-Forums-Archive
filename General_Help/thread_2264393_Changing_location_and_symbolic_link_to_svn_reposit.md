---
title: "Changing location and symbolic link to svn repository"
date: 2015-02-07
forum: General Help
---

### Post by johnson5 on 2015-02-07
Hello,

I have svn on my Ubuntu server in this location /svn

I'm running out of space I want to add a new hard drive.

I was wondering whether I can then move /svn folder to the new hard drive and then create a symbolic link to the new location so /svn will be a symbolic link to /new/hard/drive/svn

I means that I wouldn't need to change any configuration of the svn. Will this work?

Thanks,
PJ

---

### Post by Erik1984 on 2015-02-07
That should work. If the particular partition on your new drive is mounted (for example) as /mnt/newpartition then you could move the svn folder to there and make /svn a symlink to /mnt/newpartition/svn. On the Linux file system you don't directly link to the drive (or partition) like on Windows but to a mount point of that partition.

---

