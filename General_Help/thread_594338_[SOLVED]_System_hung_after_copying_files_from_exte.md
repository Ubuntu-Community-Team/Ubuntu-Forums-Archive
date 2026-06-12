---
title: "[SOLVED] System hung after copying files from external HDD, now boots to Busybox."
date: 2007-10-27
forum: General Help
---

### Post by brownbat on 2007-10-27
I was moving a large file from an external hard drive to my Ubuntu desktop and the system froze half way through, there was no response from the keyboard. I rebooted the system, but instead of loading Ubuntu, the system now shows the Ubuntu graphic and gets through the first cm of the loading bar, then boots to BusyBox.

This is on Ubuntu 7.10, with Kernel 2.6.22-14-generic.

Booting into recovery mode, here's what I see before BusyBox kicks in:
```

kinit: trying to resume from /dev/disk/by-uuid/c9b549d3-9c894b81-8a19-d71eaf752115
Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
EXT3-fs error (device hdc1): ex3_check_descriptors: Block bitmap for group 512 not in group (block 262404)!
EXT3-fs: group descriptors corrupted!
mount: Mounting /dev/disk/by-uuid/90500148-2e20-4b8c-a27c-272aabcb3e97 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

---

### Post by brownbat on 2007-10-28
Booted from CD and fscked the drive, everything's back to normal.

---

