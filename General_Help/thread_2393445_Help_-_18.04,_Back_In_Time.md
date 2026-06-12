---
title: "Help - 18.04, Back In Time"
date: 2018-06-03
forum: General Help
---

### Post by JorgeO on 2018-06-03
Hello, after upgrading to 18.04 (some bugs, same from 14.04 to 16.04) I decided to use Back In Time as an user friendly backup tool.

I'm backing up from sda Home to sdb root dir. Both are ext4.

Problem: If I do a manual backup (open BIT, click, etc) all is fine. But if I just set it up to run alone (at a given time, at boot time) there's a message stating target directory is not found.

I use BIT root.

Thanks for your help,

---

### Post by TheFu on 2018-06-04
How do you mount the target?  If it is through the fstab, all should be great.  If you are point-n-clicking ... not so much.

---

### Post by JorgeO on 2018-06-04
The Fu

Could you pls clarfy fstab?

---

### Post by Quarkrad on 2018-06-04
fstab is a text file found in /etc  i.e. /etc/fstab.  Have a look at yours - it details all the various mount points in your system; so when you power up, all these (partitions) points are automatically mounted.  It looks like you need to add your backup folder (sdb) to your fstab list.  I do something similar - (in your case) add a folder called *backup *in sdb and make it mountable in fstab (you can then back everything up to sdb/backup).  If your sdb partition/folder is not mounted then backintime sees no final destination (sdb has to be mounted before backintime is launched so backintime can see it).

---

### Post by TheFu on 2018-06-04
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) - you need a system mount, not per-userid.

And regardless of what other instructions say, use **sudoedit** to edit system files. It is the safest method available today.

---

