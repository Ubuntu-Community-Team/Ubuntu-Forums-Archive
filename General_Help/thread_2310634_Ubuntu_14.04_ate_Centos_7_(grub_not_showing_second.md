---
title: "Ubuntu 14.04 ate Centos 7 (grub not showing second Linux OS)"
date: 2016-01-20
forum: General Help
---

### Post by beep3 on 2016-01-20
I'm dual-booting Ubuntu 14.04 and Centos 7. Ubuntu was installed first.

After updating Ubuntu, grub is no longer showing Centos. My partitions are as follows:

```
/dev/sda1  (ext4, /)     400GB
/dev/sda3  (xfs)         500MB (boot)
/dev/sda4  (cryps-luks)  526GB
/dev/sda2  (extended)
  /dev/sda5  (linux-swap)  3.6GB
```

Ubuntu lives on dev/sda1 and Centos on /dev/sda4. I've tried running update-grub but this only finds Ubuntu:

```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

I then moved the boot flag to /dev/sda3, which is where grub was installed when I installed Centos. This doesn't make a difference.

Is there any way to get Ubuntu to detect Centos again?

EDIT: I just ran boot-repair. The output is at [http://paste.ubuntu.com/14587376/](http://paste.ubuntu.com/14587376/).

---

### Post by grahammechanical on 2016-01-20
I do not think that the boot flag has anything to do with it. The Grub that is installed in the MBR is looking to sda1 (msdos1) for grub.cfg. So, the Ubuntu Grub is loading.

Have you seen the recommendations of Boot Repair?

> =================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems


=================== Blockers in case of suggested repair
Please use this software in a live-session (live-CD or live-USB). This will enable this feature.


=================== Advice in case of suggested repair
You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Do you want to continue?

You did not accept the advice of Boot Repair

> ================== User settings
The settings chosen by the user will not act on the boot.
 
If re-installing the Ubuntu Grub (sda1) does not work. You might try to see if Boot Repair will re-install the Grub of CentOS (sda3) as the CentOS grub.cfg has entries for both both CentOS and Ubuntu 14.04.3.

Regards

---

