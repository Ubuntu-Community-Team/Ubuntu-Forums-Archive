---
title: "Ubuntu Server Encrypted Home Directory Backup"
date: 2015-07-09
forum: General Help
---

### Post by streat on 2015-07-09
Hello all, I have a 14.04 Server installation running that I encrypted during initial installation. I was hoping to get some advice as to the simplest secure backup solution. It is unlikely I will ever be migrating to a smaller HD so if cloning the entire drive is the best option I am not opposed to that. My main concern is ease of recovery (to decrease downtime) and the security of the backup file itself.

Can anyone provide any suggestions as to the best way to proceed?

---

### Post by TheFu on 2015-07-09
If encrypted backups is a requirement, duplicity (or a tool based on it) is the best answer.
If there isn't too much data, you can use openssl directly as a pipe thru solution for the network transport. I've only done it out of interest a few times. Never as a real backup solution.

If the file system is zfs, there are many options. 

You could use remotely encrypted storage on another box too, then just use encrypted transport like rdiff-backup to perform efficient, incremental, backups.

I just cannot recommend any image-based backup method - though they are simple. You'll need to boot off some other media, connect the other disk and use some image tool - dd, ddrescue, partimage, clonezilla, .... must be 20 others to try. These are bit-for-bit and terribly inefficient. Why copy the same bits over this week that you copied last week and last month? Sure, having 1 image can be helpful, but taking a server down just to do backups is "crazy talk."

---

