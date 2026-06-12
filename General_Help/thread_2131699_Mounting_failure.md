---
title: "Mounting failure?"
date: 2013-04-02
forum: General Help
---

### Post by Kael Seoras on 2013-04-02
When I try to start up ubuntu (10.04) I get this message.

> mount: mounting /dev/disk/by-uuid/e8d25775-db55-4f5a-bdac-19cca986fb1d on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.



BusyBox v.1.13.3 (Ubuntu 1.1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

The list of commands was pretty much Greek to me.

What gives?

---

### Post by dabl on 2013-04-02
You are going to have to boot a Live CD, browse to the hard drive and find the file /etc/fstab, copy it and paste it here, so we can see what the root filesystem looks like.  Were there any recent activities such as re-partitioning or changing/adding a hard drive, that would have affected the drive sequence and/or UUID numbers?  Does your hard drive appear in the computer's BIOS?

---

