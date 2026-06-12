---
title: "Installing from .iso on hard disk using grub..."
date: 2007-05-26
forum: General Help
---

### Post by jx2150 on 2007-05-26
Hey there-

I've successfully installed Ubuntu and Fedora from .iso files on my hard drive (no burning cds/dvds, just through Grub), but I was wondering... Is there a way to install a non-Linux OS in this same manner?

This syntax was for Fedora, for example...

title Fedora Core 6 install
        root (hd0,2)
        kernel /vmlinuz-install ro
        initrd /initrd-install.img

Would an XP or OS X .iso have compatible arguments for the kernel/initrd? Or is this just not possible the way it is with Linux distributions?

EDIT: I found this on Digg: [http://www.digg.com/linux_unix/Installing_Multiple_OS_s_Without_A_Floppy_CD_DVD_Etc](http://www.digg.com/linux_unix/Installing_Multiple_OS_s_Without_A_Floppy_CD_DVD_Etc)
Which links to howto for many different Linux distros, but still doesn't address issue of other OS's.

Thanks,
jx

---

