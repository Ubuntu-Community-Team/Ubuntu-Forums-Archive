---
title: "How can I write in recovery mode?"
date: 2008-05-26
forum: General Help
---

### Post by chrysler on 2008-05-26
Yesterday, I made some mistake settings, then my laptop with ubuntu can't startup in normal mode. So I reboot, choose recovery mode, and try to fix it. But I find that I can't write in recovery mode. Finally, I find out my ubuntu CD to fix this problem. It is so inconvenient. If I have to use the recovery mode to repair when I'm traveling outdoor and I don't bring my ubuntu CD.

It seems that the partitions are mounted as read only in recovery mode, I can't write even if I'm root in recovery mode.


Can I modify my settings again without a boot CD? 
or 
How can I modify/write in recovery mode?

---

### Post by rubicon on 2008-05-26
Try to google on "mount -rw -o remount /" :)

---

### Post by aysiu on 2008-05-26
The partitions shouldn't be mounted read-only, as far as I know.

Usually you use a terminal-based text editor like Vi or Nano. For example ```
nano -B /etc/fstab
``` or ```
nano -B /boot/grub/menu.lst
```

---

