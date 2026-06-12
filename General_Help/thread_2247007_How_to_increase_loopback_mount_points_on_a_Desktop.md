---
title: "How to increase loopback mount points on a Desktop install"
date: 2014-10-05
forum: General Help
---

### Post by MakOwner on 2014-10-05
Googling turns up several variations of editing /etc/modules or /etc/modprobe.conf.
/etc/modprobe.conf doesn't exist in the trusty (Mint Mate based on 14.04 LTS)  installation I'm running, just /etc/modprobe.d with several files there.

/etc/modules does, however, the "loop" module is not curently loaded, and I have 8 loopbacl deives available, so I suspect adding a parameter to module loading for a module that doesn't appear to exist isn't really going to help.

How the heck _do_ you increase the number of available loopback devices?

Solution:
add "max_loop={number of desire loopback devices}" to the grub command line by modifying /etc/default/grub, running update-grub then rebooting.
Example from my Mint desktop system:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash max_loop=12"

```

You can validate the change by counting the loopback devices before and after reboot:
```

$ ls -al /dev/loop*
brw-rw---- 1 root disk  7,   0 Oct  5 09:57 /dev/loop0
brw-rw---- 1 root disk  7,   1 Oct  5 09:57 /dev/loop1
brw-rw---- 1 root disk  7,  10 Oct  5 03:10 /dev/loop10
brw-rw---- 1 root disk  7,  11 Oct  5 03:10 /dev/loop11
brw-rw---- 1 root disk  7,   2 Oct  5 09:57 /dev/loop2
brw-rw---- 1 root disk  7,   3 Oct  5 09:57 /dev/loop3
brw-rw---- 1 root disk  7,   4 Oct  5 09:57 /dev/loop4
brw-rw---- 1 root disk  7,   5 Oct  5 09:57 /dev/loop5
brw-rw---- 1 root disk  7,   6 Oct  5 09:57 /dev/loop6
brw-rw---- 1 root disk  7,   7 Oct  5 09:57 /dev/loop7
brw-rw---- 1 root disk  7,   8 Oct  5 09:57 /dev/loop8
brw-rw---- 1 root disk  7,   9 Oct  5 03:10 /dev/loop9
crw------- 1 root root 10, 237 Oct  5 03:10 /dev/loop-control

```

---

