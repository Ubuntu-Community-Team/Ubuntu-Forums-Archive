---
title: "boot disk"
date: 2013-12-07
forum: General Help
---

### Post by Brotell1950 on 2013-12-07
I have received the following message

volume boot has only 11.0mb disk space remaining

How do I increase my boot disk space I have plenty of disk space to use.

Terry

---

### Post by r-senior on 2013-12-07
Could you open a terminal and post the output of this command:

```
df -h
```

It shows how your disks are partitioned and how much space remains on each partition.

Also

```
ls -l /boot
```

This shows the files in your boot directory. Running out of disk space is often caused by old kernels, which will show up in here.

---

### Post by Brotell1950 on 2013-12-07
okay I can see the old kernels what is the best way to delete them

 Terry

---

### Post by r-senior on 2013-12-08
Carefully. ;)

There is a semi-automated method described in [this thread]("http://ubuntuforums.org/showthread.php?t=2191894&p=12866952#post12866952") but check the dry-run carefully before running the command for real. See the rest of the thread for context and the link to the tutorial.

---

### Post by Brotell1950 on 2013-12-08
thankyou problem solved

Terry

---

