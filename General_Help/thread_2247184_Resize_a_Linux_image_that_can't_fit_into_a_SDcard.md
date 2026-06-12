---
title: "Resize a Linux image that can't fit into a SDcard"
date: 2014-10-06
forum: General Help
---

### Post by digiteltlc on 2014-10-06
I have a 12.04 distro running on Beaglebone board (2Gb SDcard as HDD)

I saved the whole sdcard content with 

dd if=/dev/sdb of=imagename.img

I need to burn that .img file into other 2Gb SDcards (with the inverse process dd if=imagename.img of=/dev/sdx ) but all the target ones are different in structure from original one for few kbytes less, so when i Burn them i get the "no space left on device" error message.

How can I resize the .img file to be fitted into a slightly small capacity SD ??

Thank you very much.

---

### Post by sudodus on 2014-10-06
I think it will work if you

1. Copy the first mibibyte with ***dd*** (or be prepared to install grub after copying with rsync). ***Warning***: dd is nicknamed 'disk destroyer' for a reason !!! Double-check and triple-check that the target drive is the intended target.

2. Remove the partition table and make a new one using ***gparted***. Is there a root partition with ext4 file system or a persistent live system with FAT32? Make the same kind of system and let it fill the new (alias target) SD card.

3. Copy the directory and files with ***rsync*** (when booted from another drive, and both SD cards ***mounted***. rsync copies files in the normal way, not block devices)

a. Dry run to test that it works correctly:

```
 sudo rsync -Havn /path-to-source/ /path-to-target
```

b. Real copying:

```
 sudo rsync -Hav /path-to-source/ /path-to-target
```

See ```
man rsync
``` for details.

4. If the copy does not boot, install the grub bootloader.

---

