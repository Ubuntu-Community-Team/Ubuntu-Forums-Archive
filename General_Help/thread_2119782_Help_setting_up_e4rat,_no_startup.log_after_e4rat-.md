---
title: "Help setting up e4rat, no startup.log after e4rat-collect"
date: 2013-02-24
forum: General Help
---

### Post by leonardt on 2013-02-24
so I've scanned through all the wiki's and posts to no avail.  I'm attempting to set up e4rat on Ubuntu 12.10, and after appending init=/sbin/e4rat-collect to grub, changing ro to rw, altering verbosity and log in e4rat.conf, startup.log is still failing to appear.

This is the output to dmesg | grep e4rat

```
    lenny@ubuntu:~$ dmesg | grep e4rat
    [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=D018D9CE18D9B426 loop=/ubuntu/disks/root.disk rw quiet splash init=/sbin/e4rat-collect vt.handoff=7
    [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=D018D9CE18D9B426 loop=/ubuntu/disks/root.disk rw quiet splash init=/sbin/e4rat-collect vt.handoff=7
    [   28.777556] e4rat-collect: failsafe main process (955) killed by TERM signal
    [   38.227687] e4rat-collect: lightdm main process (1217) killed by TERM signal
```

anyone think they can help?

---

