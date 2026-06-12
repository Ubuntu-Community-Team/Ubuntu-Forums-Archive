---
title: "GParted crashed and messed up my partition: What can I do?"
date: 2007-03-17
forum: General Help
---

### Post by ubu-for on 2007-03-17
I've tried to move 200 GB with GParted LiveCD to the right to get more space for my root partition. But after 11 hours and 80%, GParted crashed during copying. I've tried to undo and to move the partition back to the left but now GParted from LiveCD and Ubuntu Herd 4 crashes always within minutes.

I've seen that GParted uses "e2fsck -f -y -v /dev/sda2" to check and repair the partition. So I've opened the terminal and entered the command.

30 hours later e2fsck told me that there will be still errors but the only data I get are lots of numbers in the "lost+found" directory.

Can I do anything before I format the partition?

THX for your HELP!

P.S. No, I haven't backed up 200 GB before.

---

### Post by wpshooter on 2007-03-17
Pray that you did not have anything vital on it !!!

---

### Post by ubu-for on 2007-03-17
Some additional infos from fsck:

```
/home: Special (device/socket/fifo) inode 2455532 has non-zero size.
/home: Special (device/socket/fifo) inode 2455464 has non-zero size.
/home: Special (device/socket/fifo) inode 2456756 has non-zero size.
/home: Special (device/socket/fifo) inode 2467678 has non-zero size.
...
fsck died with exit status 4
```

What happens if I use option "-a" or the command "man fsck"?

---

### Post by ubu-for on 2007-03-18
Does really nobody have an idea how to recover some files?

THX!

---

### Post by ubu-for on 2007-03-26
R-Linux recovered 5 GB useful data and TestDisk 193 GB useless data.

Are there any alternatives?

THX!

---

