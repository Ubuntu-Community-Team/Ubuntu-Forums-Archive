---
title: "dedicated grub partition"
date: 2012-11-12
forum: General Help
---

### Post by mithun d s on 2012-11-12
$ sudo grub-install -v
grub-install (GRUB) 2.00-7ubuntu11


$ sudo grub-install /dev/sda3
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.


making a dedicated partition for grub... 
help guys..!

---

### Post by oldfred on 2012-11-12
Installing grub to a partition is not a dedicated grub partition, but just an install of grub2's bootloader to the PBR - partition boot sector.  It can be forced, but is not recommended.

Dedicated grub partitions worked with grub legacy where you could have each boot loader in each systems PBR and then chain load. But with grub2 that is not necessary, you can easily directly boot. 

You can have grub in the MBR and manually mantain a grub.cfg in one grub only partition. I in effect do this with my USB flash drives. You directly boot each install, but do not need each installs grub in the PBR.

But with grub2's os-prober you can have one grub in charge and auto find all the others. But os-prober or separate grub installs both require you to boot into each install to update grub and then your main install and update grub there also or manually update grub.

Or if you want less maintenance. I essentially do this, with a 40_custom that has all my entries to other installs and turn os-prober off.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

