---
title: "Unclean shutdown - BTRFS for / - will not mount now?"
date: 2015-02-02
forum: General Help
---

### Post by victorhooi on 2015-02-02
We have a server running Ubuntu 14.10 Server. The root filesystem (/dev/sda1) is BTRFS, as well as a swap partition (/dev/sda5).

The server was disconnected from a UPS temporarily, and then we had a power outage (what are the odds...). After turning it back on, it doesn't appear to boot:

```
error: unknown filesystem.
Entering rescue mode...
grub rescue>
```

I walked somebody through booting from a Ubuntu Server boot DVD, and going into rescue mode.

Apparently, the rescue mode wizard bombed when they actually tried to mount /dev/sda1.

We checked /var/log/syslog, and we see:

```
BTRFS: read error corrected: ino 1 of 398856193 (dev /dev/sda1 sector 795400)
<repeated twice more with different innodes and sectors>
parent transid verify failed on 397688832 wanted 901 found 408
<repeated once more with different numbers>
BTRFS: Failed to read block groups: -5
rescue: mount: mounting /dev/sda1 on /target failed: Invalid argument
rescue-mode: mount '/dev/sda1' /target failed
BTRFS: open_ctree failed
```

Any thoughts on what's going on? I'm guessing there's some kind of BTRFS filesystem corruption, possibly from the unclean shutdown?

I've been told to save btrfsck --repair for a last resort, there's apparently like things like mounting with -o recovery and btrfs-zero-log before that. 

However, curious if anybody has seen similar issues, or knows the best way to recover this?

---

