---
title: "GRUB2 error: out of disk"
date: 2013-10-12
forum: General Help
---

### Post by htorbov on 2013-10-12
I installed clean **Ubuntu Server 12.04.3 LTS** on my server using 4GB USB stick (Pendrive Linux).

```
error: out of disk.
grub rescue > ls
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1)
grub rescue > ls (hd0)
error: unknown filesystem.
```

What can I do?
I tried to re-install Ubuntu Server but the problem is the same.

**Parameters**
Processor: 1 x AMD Athlon™ II X2 260
Memory: 4 x 4GB DDR3
Space: 1 x 4TB Hard Disk

---

### Post by htorbov on 2013-10-13
Is it because the partitions? I used "Guided - use entire disk" on my 4TB hard drive.

---

### Post by slickymaster on 2013-10-13
See this: [grub error: out of disk when booting 12.04 server]("http://askubuntu.com/questions/267760/grub-error-out-of-disk-when-booting-12-04-server-with-hardware-raid5-and-gpt")

---

### Post by htorbov on 2013-10-13
This article solved my issue:
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

---

### Post by slickymaster on 2013-10-14
Glad you got it fixed. Please don't forget to mark this thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to let other people searching the forums know that it provides a working solution for this problem.

---

