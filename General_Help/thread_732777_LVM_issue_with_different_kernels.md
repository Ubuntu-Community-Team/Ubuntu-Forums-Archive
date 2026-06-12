---
title: "LVM issue with different kernels"
date: 2008-03-23
forum: General Help
---

### Post by mike503 on 2008-03-23
I created a 2 logical volumes on my system running stock Ubuntu kernels.

Right now it runs fine on: stock ubuntu kernel 2.6.22-14-server, device-mapper 4.11.0-ioctl (2006-10-12)

However, I have now compiled my own custom 2.6.25-rc6 kernel with device-mapper and all that compiled in (not module), and a slightly newer device-mapper (something like 4.14.0) - I am not booted into it right now I had to revert.

It looks like it tries to probe all devices to find any LVM2 volumes/etc and cannot find anything. I did a comparison of both kernels with a vgscan -v and there is only a couple minor things. It looks like somehow LVM2 might be wired to a UUID that changed perhaps? I can't figure out how to make this work though.

It does look like there are some odd differences worth noting:
[root@sql01 modprobe.d]# cat /proc/misc 
 63 device-mapper

on the new setup it was 61. I re-mknod'd the /dev/mapper/control file and such but it didn't seem to help, and now on reboot it's put it back to 63, so it appears to fix that itself.

What other things could it be? It seems like a flat out incompatibility but I don't understand how or why. Any information you need I will provide. Thanks

---

### Post by mike503 on 2008-03-23
Okay, well there is a workaround

murb in #device-mapper on freenode gave me this snippet:

<murb> well when it broken for me on a recent kernel disabling the sysfs_scan was sufficent to make it work.

and wham. it worked.

however this seems more like a bug/something to be addressed than some config workaround required...

---

