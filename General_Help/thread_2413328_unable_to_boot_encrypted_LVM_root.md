---
title: "unable to boot encrypted LVM root"
date: 2019-02-24
forum: General Help
---

### Post by a52ca063 on 2019-02-24
I am booting Ubuntu using GRUB without UEFI:


I thought to boot an encrypted LVM root, I had to use these arguments:

cryptopts=source=/dev/disk/by-uuid/<UUID> root=/dev/<VG>/<LV>


However, that doesn't seem to do anything and I'm not sure where I got that cmdline.  I am on Ubuntu 18.10 and with the lsinitramfs command, I can see all of the files in the initial ramdisk; however, I am unable to extract them entirely with either cpio -i, lzcat, bzcat, zcat, etc.  I was looking to see if I could extract the files in the initial ramdisk to see that init file and what the crypt arguments should be.

In any case, after it times out finding the root device, I then have the luxury to enter a shell.  In there, I manually open the device using cryptsetup and do vgchange -ay <VG> then exit.  After I exit, the boot process continues as expected.

In summary:

1. what is the right argument(s) to pass to have the initramfs ask me to unlock the encrypted volume?
2. since I'm on Ubuntu 18.10, I thought the initramfs was compressed with lz4, I also tried lz4 <initrd> | cpio -i and lz4 also complained about the init not being an lz4 file.  My initramfs is 55MB which is rather large, but that may also be because it probably has every possible module under the sun.


Walter

---

