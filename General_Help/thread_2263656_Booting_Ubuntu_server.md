---
title: "Booting Ubuntu server"
date: 2015-02-02
forum: General Help
---

### Post by alasdair3 on 2015-02-02
I'm running Ubuntu server 14 from 16gb USB and have run into a problem where the system wont boot. I can run a live session from usb but my main installation isn't recognised as bootable media.

I'm trying to reinstall GRUB to fix the problem but am struggling with some of the basics. If anyone could answer some of these small queries I'd be extremely grateful.

1. I think my original installation was done in UEFI mode but am not 100% sure. How do I tell and how will this affect re-installing GRUB 2?

2. During the Ubuntu server installation I used the default partitioning scheme with LVM. Now I'm not sure exactly what some of these partitions are:
    a) a 512mb FAT32 partition with a "boot" flag. Is this the EFI system partition? Is it supposed to contain anything as at the moment this partition is empty?
    b) a 256mb ext2 partition with GRUB and EFI directories as well as other files. If the first partition is for booting from then I don't know what this one is for.
    c) ~15gb lvm partition with /root, /home and /swap. I know that this contains the system files but there's also a /boot folder. I'm not sure exactly what the role of this is?

3. Based on the above info, where exactly do I need to re-install grub to get the system to boot? Is this guide appropriate: [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)

Many thanks in advance for your help. It's very much appreciated.

---

