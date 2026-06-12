---
title: "Disaster recovery approach advice"
date: 2008-01-15
forum: General Help
---

### Post by ksadil on 2008-01-15
I have installed Gutsy on a partition that takes up half og the hard disk. The other half is a free space partition called mirror mounted under /mnt. I have been doing a rsync from / to the mirror partition. I have an external 300G hdd with ntfs filesystem, and I tar the mirror up into one file on the external hdd. Then I burn the file to a dvd. 

I am interested in comments about whether it is a good approach, overkill, or is there a better way. This is my web server, mail server, etc, so I am sensitive to uptime and archive integrity. Any thoughts, suggestions or comments are appreciated. If I wanted to restore the whole system to a new hard disk would it be as simple as rsyncing back to the same partition on a fresh gutsy install, or would there be things to be wary of?  

Regards,
Kim

---

