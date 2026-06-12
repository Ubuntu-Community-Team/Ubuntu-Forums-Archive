---
title: "Accessing ZFS via NFS: Operation not permitted"
date: 2016-07-18
forum: General Help
---

### Post by danBhentschel on 2016-07-18
I have a 16.04 machine running a large ZFS filesystem that is shared via NFS (zfs set sharenfs="rw,insecure" storage) with several other systems. Today I decided to update the software on all my machines and reboot everything. After I restarted all the systems, all of my 16.04 machines can no longer access the NFS share. If I try to cd into any directory, it will respond "-bash: cd: /storage/www/: Operation not permitted".

This does NOT happen on any of my non-16.04 machines. I have a 14.04 that can access all directories of the NFS share just fine, and I also have a 15.10 system that has no problems either.

I don't see any pertinent messages in the syslog for either the NFS server or client machine. I figured out that I **CAN** access the NFS directories as root on the 16.04 machines, and then **after** I have done so, then the NFS share is accessible to other users as well.

Any advice?

 - danBhentschel

---

### Post by Reinhard Zierke on 2016-07-19
I get the same error message "cd ... Operation not permitted" when my PCs were upgraded to kernel 4.4.0-31.  I can cd into the
filesystem as root with mounts the NFS4 subvolume in question, and can after then cd into the directory as a normal user.

The error disappeared when I booted my PC back to kernel 4.4.0-28.

---

### Post by danBhentschel on 2016-07-19
Thank you so much! You are absolutely right. As soon as I downgraded my machines to the previous kernel version (a mix of -22, -23, -24, and -28) all of them started acting correctly again.

 - danBhentschel

---

### Post by pHr34kY on 2016-07-21
Seriously?!

I updated to 4.4.0-31 at the same time that I was reconfiguring my NFS exports to automount NFS4 over IPv6... and I've been up for 3 nights trying to figure out what I changed that broke it. This was the last thing I would have thought about rolling back.

Someone should file a bug report or something. EDIT: [Someone has.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1603719")

On a side note, you don't get this error once you 'su' to root.

---

