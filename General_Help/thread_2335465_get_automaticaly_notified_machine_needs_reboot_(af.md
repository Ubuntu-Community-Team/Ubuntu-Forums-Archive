---
title: "get automaticaly notified machine needs reboot (after auto security updates)"
date: 2016-08-29
forum: General Help
---

### Post by roberto32 on 2016-08-29
I checked in software sources t automaticaly download and install security updates. That's great but the problem is that it won't get me notified that my machine needs reboot. I've made a script which checks this - but it needs to be "invoked" manually. How to get auto notified after sec updates are installed and machine needs reboot? Hint I'm using Xfce
Thanks Rob :)

---

### Post by TheFu on 2016-08-29
Whenever I open a terminal on the machine or ssh in from another machine, I'm notified.
```
$ ssh romulus

Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-93-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

New release '16.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

*** System restart required ***
Last login: Sun Aug 28 22:00:47 2016 from 172.22.22.253
```

You could change the root window (i.e. desktop background) if the /var/run/reboot-required file exists. Just check that every 30 minutes. I use 'feh' to do that, but never though to change the background, since rebooting is something I'd only do on a weekend.

However, this system really doesn't need to be rebooted. The kernel hasn't changed since 7/18. I removed some old kernels from the system, grub got updated to remove them from the grub boot menu, but there isn't any reason to reboot the machine even though that reboot-required file was created. Computers are dumb.  I rebooted on Saturday morning (actually swapped out a failed disk in a RAID array) and uptime shows this, so I'm positive it was recently rebooted.

Computers are dumb.

---

### Post by grahammechanical on 2016-08-29
I believe that the Linux kernel developers have done a lot of work to make it possible to upgrade the kernel without requiring a restart. I am not sure if this function is active in the kernel versions that the Ubuntu kernel team push out. But we should at some point in time be seeing less requests to restart.

That being said whilst running both the xenial & yakkety development versions and doing daily updates I have seen lots of requests to restart. I think this is coming from updates to systemd as there was no update to the kernel at the same time.

[http://www.linuxjournal.com/content/no-reboot-kernel-patching-and-why-you-should-care](http://www.linuxjournal.com/content/no-reboot-kernel-patching-and-why-you-should-care)

Regards

---

