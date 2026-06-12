---
title: "Xen: How to setup Ubuntu 6.10 (Edgy Eft) perfectly as Xen gest domain (DomU)?"
date: 2006-10-28
forum: General Help
---

### Post by fuzziefuz on 2006-10-28
Hi,

I just managed to setup Xen 3.0.3 with the new Ubuntu 6.10 (Edgy Eft) as host operating system (Dom0) - was pretty simple following the instructions at [https://wiki.ubuntu.com/XenOnEdgy](https://wiki.ubuntu.com/XenOnEdgy).

But I did not find a documentation on how to setup Ubuntu 6.10 (Edgy Eft) as a guest domain (DomU). So I followed this guide (for Breezy and Dapper) [https://help.ubuntu.com/community/XenOnUbuntuBinaryInstall](https://help.ubuntu.com/community/XenOnUbuntuBinaryInstall) and used debootstrap to install edgy from CD mounted at /media/cdrom to my LVM volume at /xen/guest:

```
debootstrap --arch i386 edgy /xen/guest file:/media/cdrom
```

After that I mounted /xen/guest and configured the guest system (copied the kernel modules, set hostname, disabled tls, etc.)

Finally I created the configuration file for the guest (/etc/xen/guest) and booted it up.

The guest domain boots up, but it hangs a long time (several minutes) at "Begin: Running /scripts/local-top ...". Then it boots up completely without an error message.

Any idea why /scripts/local-top takes so long?

I found out that this script belongs to the init ramdisk and is located at /usr/share/initramfs-tools/scripts/local-top and contains a script named udev.

Greetings and thanks for your comments

---

### Post by jonoinsa on 2006-10-30
I am experiencing exacly the same symptom....looking deeper into the "problem"....

---

### Post by fuzziefuz on 2006-10-30
Hi!

I solved the problem as follows:

I removed the "md" and "lvm" scripts (make a backup copy of them!) from /usr/share/initramfs-tools/hooks and /usr/share/initramfs-tools/scripts/local-top on the host operating system (Dom0) and created an own init ramdisk for the guest operating systems (DomU's)

```
mkinitramfs -o /boot/xenU-linux-2.6.17-6-generic-xen0.initrd.img 2.6.17-6-generic-xen0
```

After that you should restore the "md" and "lvm" scripts from your backup, we just wanted them not to be in the init ramdisk for our DomU's, but maybe you need to recreate the init ramdisk for your Dom0 anytime.

Finally adopt your DomU's config files to point to the correct init ramdisk we just created for them (in my case /boot/xenU-linux-2.6.17-6-generic-xen0.initrd.img).

The DomU's are booting now much faster :-)

I hope this saves a lot of people a lot of trouble in the future. Have a nice day.

---

### Post by kasper22 on 2006-12-02
fuzziefuz, it worked like a charm thank you for posting.

---

