---
title: "Problems installed a different bootloader"
date: 2013-01-25
forum: General Help
---

### Post by Xanthius on 2013-01-25
Hey guys,

I'm having issues installed the boot manager burg, which is a bootloader with (to my opinion) a better interface grub has to offer.

My system is partitioned as followed according to GParted.

/dev/sda1 - ntfs - boot
/dev/sda2 - extended
  /dev/sda5 - ext4 - mountpoint /
  /dev/sda6 - unknown (this was intended to be a swp partition)

According to [this]("http://www.unixmen.com/how-to-install-burg-in-ubuntu/") guide it's done in a few simple commands, however I have multiple HDD's in my system, so "hdd0" is obviously wrong, and should be dev/sda1. However upon doing that it gives me a warning.

```
root@L702X:/home/someuser# burg-install /dev/sda1
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
```

So currently, I have no clue what arguments I should use. If I let the program self-determin on where to install it, it does not seem to work, because it broke grub (low resolution, black white text), and not loading burg.

Can anyone help me resolve this issue?

---

### Post by oldfred on 2013-01-25
You should not install a boot loader to a partition, but to a drive. Generally I recommend installing the boot loader to the same drive as your install and having different installs on different drives so when one drive fails you can still boot the other drive.

I also thought that burg is not maintained any more and may not work with the newest grub2 with sub menus.

With grub the boot drive in BIOS is always hd0, but if you have multiple drives you can install a boot loader to any drive. Or sda is not always hd0 in grub. 
 I normally boot from sdc and in grub have chain load entries to other MBRs in my 40_custom. But those chain loads can change depending on which drive i boot from or I have to manually adjust my standard 40_custom in that install.

---

