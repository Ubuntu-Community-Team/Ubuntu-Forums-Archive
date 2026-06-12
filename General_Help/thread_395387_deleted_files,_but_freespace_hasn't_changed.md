---
title: "deleted files, but freespace hasn't changed"
date: 2007-03-28
forum: General Help
---

### Post by kpagpa on 2007-03-28
Hi everyone,

I need some help with a free space problem.

I noticed today that my ubuntu partition was filling up, so I checked my var/backup folder to find that there was 8Gb of backups!  Being rather silly, I went to the terminal and did gksudo nautilus, went into the folder, manually deleted the backups and then cleared the trash folder.  My system still shows that there is 95% of the partition being used, but at least half of that was the backups.

I know I should have purged the backups in sbackup, but I didn't know that at the time! ](*,)  dohhhh!

Why hasn't it changed?  Is there anyway to get the system to 'see' the free space that should be there?

Thanks for your help!

---

### Post by Gannin on 2007-03-28
Did you check to see if there was a .Trash directory in /root?

---

### Post by fanatik on 2007-03-28
Usually if you delete a file and the space doesn't get cleared its because a running process might still be hanging on to that file. 

However I don't suppose this is the case here, type the following in a terminal and paste the output:

cd /var
du -hs backups/       # (or whatever folder name was)
df -h .

Cheers,
James.

---

### Post by kpagpa on 2007-03-28
Thanks very much Gannin and James for your replies, I appreciate both of you taking the time to help.

I checked the root directory - the files are in the .Trash folder there, so it didn't really delete them.

I hope this helps other people with the same problem.

:)

---

### Post by Gannin on 2007-03-28
You're very welcome :).

---

