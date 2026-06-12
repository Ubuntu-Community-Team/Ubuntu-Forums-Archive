---
title: "input/output error using cp command"
date: 2023-10-06
forum: General Help
---

### Post by anmac1789 on 2023-10-06
hello everyone I am using ubuntu 23.04 kernel version 6.2.0-20-generic and I am having a problem using cp to copy .mp4 files. I am getting ```
cp: error reading './xxxxxxx.mp4': Input/output error
```

---

### Post by TheFu on 2023-10-06
What's the media source?
What the source file system?
I suspect it is a flash drive with a crappy file system that has been corrupted.  That happens from time to time.  If you** ls -al** on the full directory, I bet other attributes like the permissions are corrupted too.

Whenever that happens to me, which is about 2x a month, the only solution is to forget those files and reformat the partition.

---

### Post by yancek on 2023-10-07
It is generally a good idea to post the command you ran as well as the error you get if you want help.  The answers to the questions in post 2 will likely be useful.

---

