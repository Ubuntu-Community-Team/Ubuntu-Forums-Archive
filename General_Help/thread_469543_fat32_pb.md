---
title: "fat32 pb ?"
date: 2007-06-10
forum: General Help
---

### Post by chpnp on 2007-06-10
Hi,

I set up  my dual boot XP/Ubuntu system so that I can share both the email and mozilla profile by moving their files to a shared fat32 partition.
Everything works almost well, in that I can access data from both systems

However when I shutdown my ubuntu system and restart XP, XP complains that the shared fat32 requires chkdsk, which seemingly results in the loss of some portion of the file (I know it from the last email that I received that was truncated (chkdsk says it has adjusted the inbox file and several files from FF).
It is not the first time I am seeing this problem.

It also said that the file \System Volume Information\_restore\<whatever> had a problem that it fixed. i have a suspicion that this might be an older problem than just switching from XP to linux then back to XP for that reason, but I am not sure how to interpret that.

I am not sure if this is a mozilla suite pb or a fat32 pb that I have, anyway any thought will be greatly appreciated....


Thanks

Christophe

---

### Post by chpnp on 2007-06-10
I think I can reply to my own question.
I have been using from time to time  the hibernate function of windows (or linux) to speed up the process.
Not a very good idea on shared files.

I will do some further tests. 
In the meantime, I would be interested in any feed back if
- you ever had problems with Fat32 FS
- you decided to use an Ext2 FS driver under XP and are happy with your choice (happier than using fat32 for example), and why ? and what driver did you use.

Thanks.

Christophe

---

