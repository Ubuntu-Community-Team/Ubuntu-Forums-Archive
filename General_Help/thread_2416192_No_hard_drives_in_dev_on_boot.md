---
title: "No hard drives in /dev on boot"
date: 2019-04-06
forum: General Help
---

### Post by rsteinmetz70112 on 2019-04-06
I have a a badly broken system. Upon booting I get an error 
[o.oooooo] do_IRG no IRG handler for vector
followed by an error that the system can't connect to lvmtetad
It them drops into the initramfs shell.
looking in /dev there are no sd devices,
Something is preventing the system from recognizing the hard drives.
blkid does not list any devices.

---

### Post by Rubi1200 on 2019-04-07
I recommend booting from a live environment and posting the results of the boot info summary (see link in my signature).

Please also post system specs. especially RAM, graphics card, CPU etc.

Thanks.

---

### Post by Dennis N on 2019-04-07
Apparently you can reach the grub menu and start booting an OS?

You could try this one-time test: At grub menu press 'e' to edit the desired menu entry.
add **pci=nomsi,noaer** after **quiet splash**
press **ctrl+x** or **F10** to attempt boot.

If that works, ask about editing /etc/default/grub to permanently add this to menu entry.

---

### Post by rsteinmetz70112 on 2019-04-08
Thanks for the replies.
 
The problem was that the system was not identifying the block devices in /dev in particular sd[a-d] and the partitions on them. Obviously mdadm could no assemble the arrays and lvm2 could not see the vgs without those devices.

I've managed to fix it. I booted into the live environment mounted the local file systems downloaded the packages below:

```

#apt download <package name>

 initramfs-tools_0.130ubuntu3.6_all.deb
 linux-firmware_1.173.3_all.deb
 linux-headers-4.15.0-47-generic_4.15.0-47.50_amd64.deb
 linux-image-4.15.0-47-generic_4.15.0-47.50_amd64.deb
 linux-modules-4.15.0-47-generic_4.15.0-47.50_amd64.deb
 linux-modules-extra-4.15.0-47-generic_4.15.0-47.50_amd64.deb
 linux-tools-4.15.0-47-generic_4.15.0-47.50_amd64.deb
```

Then ```
chroot
``` and installed them them using ```
apt install --reinstall /root/<package  file name>.deb
```

I'm not sure which one or ones fixed it but since they were the original installed packages I figured there was no harm in reinstalling them

---

