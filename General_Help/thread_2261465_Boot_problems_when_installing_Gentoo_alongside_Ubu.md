---
title: "Boot problems when installing Gentoo alongside Ubuntu"
date: 2015-01-19
forum: General Help
---

### Post by NilPointer on 2015-01-19
Yesterday, I've attempted to install Gentoo on my machine. I managed to install a working Gentoo in the end, but I've messed up boot pretty badly. While installing bootloader, I've put Gentoo's kernel and initrd onto boot partition (one I used for Ubuntu and wanted it to be shared with Gentoo) and ran grub-mkconfig to generate new config. But it worked differently from what I've expected and generated config only for Gentoo. There still were Ubuntu's vmlinuz and initrd on boot partition, but grub-mkconfig detected those images as Gentoo GNU/Linux. I tried to move Gentoo's kernel and initrd from boot partition, update-grub found then Ubuntu images, but now neither Gentoo nor Ubuntu will boot (grub shows "File not found" and puts me into grub rescue mode). Moving files back doesn't help. So, I've pretty much locked myself out from Ubuntu and Gentoo, too, left only with Ubuntu LiveUSB.

---

### Post by NilPointer on 2015-01-19
Another attempt to fix boot by chrooting into Ubuntu. Reinstalled grub onto /dev/sda, ran update-initramfs, then ran update-grub.

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.17.7-gentoo
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found memtest86+ image: /memtest86+.bin
Found Gentoo Base System release 2.2 on /dev/sda10
done
```

Will check if it's fixed.

UPDATE: It's better now, now I could boot both into Ubuntu and Gentoo. However, now there's tons of invalid options, such as booting Gentoo with Ubuntu's kernels as well as booting Ubuntu with Gentoo kernel.

---

### Post by NilPointer on 2015-01-19
Hmm, I've managed to restore Ubuntu's GRUB 2 to initial state and installed separate GRUB 2 into /boot on Gentoo's root partition. I think all that remains is to add option to chainload Gentoo's loader from Ubuntu's GRUB.

---

### Post by NilPointer on 2015-01-20
os-prober seems to work very strangely. Updating GRUB gives promising output:

```
Generating grub.cfg ...Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.bin
Found Gentoo Base System release 2.2 on /dev/sda10
done
```

But it generates Gentoo's menu entry as "Ubuntu, with Linux 3.13.0-43-generic (on /dev/sda10)". I wonder why does it call it Ubuntu despite os-prober tells that it has found Gentoo Base System. Moreover, it still generates entries for Ubuntu with Gentoo kernel and Gentoo with Ubuntu kernel. Wonder how to explicitly specify which kernels go to which distro.

---

### Post by oldfred on 2015-01-20
You cannot share a /boot partition. If you really want /boot partitions you must have one for each install. Generally better not to have /boot partition at all, unless using LVM, or a server type configuration.
If you attempt to share you get the issues you have with conflicts and if one install happens to have the same version it gets even worse. And each is overwriting the part that is grub in /boot and will show all kernels, even though some are really for the other install.

---

### Post by NilPointer on 2015-01-21
Oh, I see. Thanks for your reply.

I've merged /boot partition back into Ubuntu's root partition (because I've separated it for multibooting different distros in first place, but seems I've understood everything wrong way).

But then another problem emerges. Looks like best option is to chainload Gentoo GRUB2 from Ubuntu's GRUB2. However, GRUB2 doesn't want to be installed to sda10 partition (Gentoo's one). It exits with error because

> warning: File system `ext2' doesn't support embedding.

How to build chainloading GRUB setup now? GRUB2 is installed onto Gentoo partition and there's proper grub.cfg there, but without core bootloader code it won't be chainloadable, would it?

I've got a non-EFI (BIOS) system with MBR on drive.

---

### Post by oldfred on 2015-01-21
I used chainloading with grub legacy and originally did not like grub2 as it was not as good for chainloading. But now find grub2 does a lot more.
But it should let you directly boot without a chainload.
Or you can boot the partition if Gentoo is like Debian based that have a link to most current kernel in /. 

In Ubuntu's 40_custom copy the boot stanza from Gentoo's grub menu and run sudo update-grub to update Ubuntu to include the new entry.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by NilPointer on 2015-01-25
Looks like problem fixed itself in the end, when I've repeated Gentoo installation procedure from scratch. Not sure what was wrong, but now main GRUB 2 seems to correctly detect and add Gentoo to the boot list.

---

