---
title: "fail to boot - grub rescue"
date: 2015-07-30
forum: General Help
---

### Post by Sparrow318 on 2015-07-30
Hi,
I had dualboot with windows and linux, I tried to change size of windows C: volume and after reboot, it doesn't load ends with grub rescue shell.

If I trun on UEFI boot in BIOS it ends with "No bootable device -- insert boot disk and press any key"

from grub rescue I am able to start my installed linux by this:
```

set prefix=(hd0,7)/boot/grub
set root=(hd0,7)
insmod (hd0,7)/boot/grub/x86_64-efi/linux.mod
linux /vmlinuz root=/dev/sda7
initrd /initrd.img
boot

```

I also tried ubuntu boot repair disk, fixmbr by windows recue console.
When I try to install new windows, an error appears - "indows cannot be installed to this disk. The selected disk  is of the GPT partition style."

I'd really appreciate if anyone would help me with this,
thank you.

edit: here is boot info [http://paste.ubuntu.com/11964754/](http://paste.ubuntu.com/11964754/)

---

### Post by leunam12 on 2015-07-30
Your Hard Drive has a GPT partition table, it works with UEFI. Change your BIOS settings to UEFI before attempting to re-install Windows.

---

### Post by Sparrow318 on 2015-07-30
I can't boot from CD, when UEFI boot is enabled.

---

### Post by yancek on 2015-07-30
You have combined MBR/UEFI boot which almost always leads to problems such as you are having.   Your windows install (windows 8??) has EFI files on a separate Efi partition.  You can also see the Linux files there.  You have windows code in the master boot record of the primary drive.  You should not have that if you are using UEFI/GPT to boot.  My understanding is that if you are using GPT with windows 8, you need to use UEFI.  I don't use UEFI myself so I'm not sure how that would be changed.  Also, if you take a look and according to the boot entry you posted, your Kali install is on sda7 and the grub.cfg entries all point to sda5.

---

### Post by oldfred on 2015-07-30
Your sytem is UEFI and your installs are UEFI. But you also installed BIOS boot loaders to MBR which will not work. Do not try to boot in BIOS mode.

Some systems require you to turn on boot from USB, if you upgraded UEFI/BIOS it will reset back to defaults and you may have to turn it on again.
Best to make sure secure boot is off in UEFI, UEFI is on, and CSM/BIOS/Legacy is off.

You should boot Boot-Repair in UEFI mode to make UEFI repairs.

To make Windows repairs you need to boot it in UEFI mode.
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

---

### Post by Sparrow318 on 2015-07-30
Thank you very much for your help, I made live USB with boot-repair and it worked like a charm.

---

