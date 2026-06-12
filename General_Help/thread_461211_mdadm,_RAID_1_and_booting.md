---
title: "mdadm, RAID 1 and booting"
date: 2007-06-01
forum: General Help
---

### Post by jintxo on 2007-06-01
Hello fellow users,

I have installed a 7.04 "server" ubuntu distribution with 2 identical Hard Drives. Both are SATA II.

I have set up a software RAID 1 through mdadm and use of the md devices during installation and the software RAID works great (as expected).

Now I go to test the RAID, expecting that the system would boot with 1 of the drives not plugged in. 

What I am seeing is that if I plug in sdb and not sda, my system boots normally with degraded RAID devices; everything works fine.

If I boot with sda plugged in and sdb un-plugged, my system won't boot and after a fairly long time-out it drops me to an initramfs busybox environment, where I can't acheive much.

It was my understanding that this should work either way (I do rebuild the RAID arrays between each test to ensure a known starting point) and the system should boot with with sda or sdb failed.

Anyone have any insight? The first messages I see after the time-out are:

Usage: modprobe [-v] [-V] bla bla bla (like a failed modprobe command)
mount: cannot read /etc/fstab: No such file or directory
<more mount errors stating no such file or directory>
Target Filesystem doesn't have /sbin/init

and then I get the busybox shell :-(

I would really need this to work, as the server will be unattended for long periods of time in a place where the electricity is not reliable.

Cheers and regards,

Cedric

---

### Post by jintxo on 2007-06-04
Justi n case you read the post and are about to reply: Please ignore it.

 I installed debian instead and everything worked like a charm. I guess I'll stick to debian for my servers for the time being (I use ubuntu on my desktops)

:-)

---

