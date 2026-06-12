---
title: "Ubuntu ArmHF 12.10 Omap4 Grub Boot Command Hang - MS Surface Mod"
date: 2018-04-07
forum: General Help
---

### Post by jacobcmcqueen on 2018-04-07
Hello!!! Glad I could be here.

Basically, I managed to get a grub bootloader on a surface RT (15xx series with cortex-a9 tegra 3 processor.)

I can chainload bootarm.efi (for some reason?) and that works fine. But well, I've been trying to unsquashfs the filesystem from the casper folder in the Ubuntu 12.10 ArmHF Omap4 image and boot the initrd and vmlinuz from within it.

Well, secureboot is forced to be semi-enabled. But I'm in grub....

The main issue is when I initiate the 'boot' command, the system does nothing. It just sits there, is it loading something?

Here's my boot process:

```

[B]0. (Prefix mods directory doesn't exist in this EFI modification, when I add it, I get stuck on the surface logo)
1. set root=(hd0,gpt2)
2. insmod normal
3. normal
4. insmod linux
5. linux /boot/vmlinuz
6. initrd (hd0,gpt2)/boot/initrd.img
7. insmod ext2
8. insmod all_video
9. insmod part_gpt
10. insmod part_msdos
11. insmod fat
12. devicetree (hd0,gpt1)/tegra30-colibri.dts (brought over from u-boot device trees)
12. boot

????????

Nothing happens.
[/B]
```


My squashfs was extracted onto a ext2 partition on a thumb drive (hd0,gpt2), (hd0,gpt1) is the fat32 partition containing my efi files needed to boot grub..


I'm not sure, basically, I know they don't make memdisk for armhf....

The behavior seems to be conistent across every O/S I've tried loading the initrd and linux kernel. I go through the process, nothing happens.



However, I did try and boot a grubarm.efi I installed after compiling grub-install with target=arm-efi but I kept getting "Could not load image" problems, however, chainloading bootarm.efi worked and brought be back into grub.



Not sure, any help is appreciated. I really DO NOT want to re-compile this grub.efi as I have almost no idea how it's setup but if you want to take a look the files are here:

[https://forum.xda-developers.com/attachment.php?attachmentid=4236587&d=1502266883](https://forum.xda-developers.com/attachment.php?attachmentid=4236587&d=1502266883)


[B]
Thanks :))))


Edit: Added devicetree command

Edit: I noticed if I set my terminal_output console instead of gfxterm the behavior is almost the same. Is this simply the terminal_output being directed to console after the boot command? How can I keep it on gfxterm?[/B]

---

