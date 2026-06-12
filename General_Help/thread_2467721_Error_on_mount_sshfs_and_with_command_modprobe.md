---
title: "Error on mount sshfs and with command modprobe"
date: 2021-10-06
forum: General Help
---

### Post by z2m on 2021-10-06
Hi all,

I'm here today because i have errors on my ubuntu server since a hard drive crashes.

First, the ubuntu version. DON'T HIT ME !!! If i could i would do an update, but my client feels "it's not a priority"
My server is on Ubuntu 12.04.5 LTS.
uname -a say Linux ##########.ovh.net 3.2.13-xxxx-std-ipv6-64 #1 SMP Wed Mar 28 11:20:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux if it can help

Last week, a hard drive crashes, OVH replace it, and i've rebuild the 2 raid arrays.

Now, i see that a custom backup copy script dont work because it cant connect to a distant server with sshfs.

Here's the command used and some tests :

Command : sshfs backup@__DISTANT_IP__:/home /media/srv_backup
Result : fuse: device not found, try 'modprobe fuse' first

Command : modprobe fuse
Result : FATAL: Could not load /lib/modules/3.2.13-xxxx-std-ipv6-64/modules.dep: No such file or directory

Command : ll /lib/modules/
Result : the directory is empty

Command : lsmod
Result : Opening /proc/modules: No such file or directory

Can you help me to correct this ?

Thanks

---

### Post by TheFu on 2021-10-06
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) moving to a supported release NEEDS TO BE A PRIORITY.

Nobody can test a similar setup and cannot help, since we don't run unsupported releases. Sorry.

There are better ways to do backups than by remote mounts (of any sort), BTW.  But you'll keep running into the "unsupported" problem, regardless.

---

