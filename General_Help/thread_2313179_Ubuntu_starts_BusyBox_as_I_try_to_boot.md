---
title: "Ubuntu starts BusyBox as I try to boot"
date: 2016-02-10
forum: General Help
---

### Post by Jasper_Haller on 2016-02-10
Dear all,

I would appreciate your help with the following issue.

As of this morning, I can no longer boot. I had logged off from my computer; when I tried to log back on, nothing happened. Whenever I try to re-start my computer, after entering the passphrase for my hard disk, the following output appears on the screen:

```

mount: mounting /dev/mapper/ubuntu--vg-root on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.


BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

I've done some googling, and found this, which looks very similar:
 [URL="http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs"]http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs
[/URL]
So I downloaded Ubuntu Boot-Repair, installed it on a USB stick, and ran it. I selected "recommended repair", and received a message that the repair had been successful. The log is here:
[http://paste.ubuntu.com/15007879/](http://paste.ubuntu.com/15007879/)

However, this has not solved the issue, and I still end up in the BusyBox whenever I try to boot.

If anyone has any pointers, I would much appreciate it.

Cheers,
Jasper

---

### Post by Jasper_Haller on 2016-02-12
Update: I should have seen this earlier. This person seems to have the same symptoms as I have:

 [URL="http://askubuntu.com/questions/17647/target-filesystem-doesnt-have-requested-sbin-init?rq=1"]http://askubuntu.com/questions/17647/target-filesystem-doesnt-have-requested-sbin-init?rq=1

[/URL]But following the instructions provided in the answer has not made a difference, even though fsck came back without an error code. Likewise, the variation suggested here has been fruitless:

[https://tdapower.wordpress.com/2011/07/11/solution-for-ubuntu-target-filesystem-doesnt-have-sbininit/](https://tdapower.wordpress.com/2011/07/11/solution-for-ubuntu-target-filesystem-doesnt-have-sbininit/)

I am starting to get worried a bit. If nobody knows of a solution, what should I do? First, is there a way to recover my data? I tried the simple-minded thing and attempted to access my hard drive after booting from a Live CD, but all that happened is that the icon disappeared. Second, can I get my computer running again by re-installing Ubuntu, or do the signs point toward a deeper issue with my hard drive?

---

