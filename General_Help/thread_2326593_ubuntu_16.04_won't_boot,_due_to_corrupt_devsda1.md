---
title: "ubuntu 16.04 won't boot, due to corrupt /dev/sda1"
date: 2016-06-02
forum: General Help
---

### Post by castromic on 2016-06-02
I have been successfully using 16.10 for some time now. The system doesn't now boot due to a corrupt /dev/sda1 file system. The screen error message is :-

/dev/sda1 contains a file system with errors,check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
          (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on dev/sda1 requires a manual fsck

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) _

Entering help brings up a long list of commands - non of which include RUN.

Any help would be much appreciated.

---

### Post by ajgreeny on 2016-06-02
*Thread moved to **Ubuntu Development Version**.*

---

### Post by grahammechanical on 2016-06-02
The command is

```
fsck
```

If you can load a recovery mode kernel from Advanced options for Ubuntu you will see that the recovery menu has an option called fsck - check all file systems. An alternative is to load the live session but do not mount the 16.10 partition and then open a terminal and run the fsck command using /dev/sda? to point to the partition.

**Case 3**

> User may run fsck against any filesystem that can be unmounted on a  running system. e.g. if you can issue umount /dev/sda3 without an error,  you can run fsck against /dev/sda3.

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

Oh, status code 4 = file system errors left uncorrected. Be ready to reinstall.

Regards.

---

### Post by castromic on 2016-06-05
Sorry my typo mistake, my version is 16.04.  Unable to run fsck as no run option in 'initramfs'.

I suspect I may have a hardware problem as iso disk will not load from dvd drive either.

 Will investigate.

---

### Post by X-RED_Tech on 2016-06-05
> **castromic said:**
> I suspect I may have a hardware problem as iso disk will not load from dvd drive either.

 Will investigate.

Depending on how it was burned it may not boot. And perhaps with USB flash it's faster.

---

### Post by swati3 on 2016-06-21
I had the same problem and my problem was solves by manually running:
fsck /dev/sda1
After pressing enter it will prompt you several times, write yes to every prompt.

---

### Post by ventrical on 2016-06-21
> **castromic said:**
> Sorry my typo mistake, my version is 16.04.  Unable to run fsck as no run option in 'initramfs'.

I suspect I may have a hardware problem as iso disk will not load from dvd drive either.

 Will investigate.

Can you give us a brief hardware profile?

regards..

---

