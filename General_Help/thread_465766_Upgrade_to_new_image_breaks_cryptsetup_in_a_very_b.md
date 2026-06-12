---
title: "Upgrade to new image breaks cryptsetup in a very bad way"
date: 2007-06-06
forum: General Help
---

### Post by jenred on 2007-06-06
Applied latest updates :

linux-headers-generic (2.6.20.15.14) to 2.6.20.16.28.1
linux-image-generic (2.6.20.15.14) to 2.6.20.16.28.1

Booted into new image entered my LUKS passphrase -- and found myself with a not so great error -- along the lines of fsck failed no filesystem found, apt not installed and dropped me into  shell.  If I  continue the boot my encrypted partitions fail to mount.

Anyone experiencing a similar issue? :(

---

### Post by snobel on 2007-06-06
> **jenred said:**
> fsck failed no filesystem found, apt not installed and dropped me into  shell.  If I  continue the boot my encrypted partitions fail to mount.
Maybe you forgot to change the 'kopt' line in /boot/grub/menu.lst when you encrypted your root partition?
In that case the kernel install, which updates menu.lst, will probably have changed the root back to whatever it was before. So when fsck tries to check the partition, it finds a luks filesystem that it doesn't recognise, and fails...

If you boot, hit esc to get the grub menu, select the -16 kernel and hit 'e', then you can check if the kernel line contains something like root=/dev/mapper/<your encrypted root>. If it does, then something else is wrong. If the root is specified by UUID or a device name like /dev/sda1 then hit 'e' again and edit the line to point to your mapped device, then hit enter, and 'b' to boot.

If you can't remember the mapping name, try to boot on the -15 kernel, which may work. If that fails you will probably need to boot a live cd and install cryptsetup to be able to check /etc/crypttab on the root.

---

### Post by jenred on 2007-06-07
Hi thank you very much for your reply. Turned out it wasn't related to cryptsetup, it was a ICH4/5 bug that is also biting many other people:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996)

Thanks again,

Jen

---

