---
title: "Laptop freeze on restart"
date: 2014-10-09
forum: General Help
---

### Post by Sparrowhawk536 on 2014-10-09
My laptop hangs after I choose restart. Exactly at the time when he should power off. If I choose shut-down, it power-off without any problem. I tried modify grub file like this: > [COLOR=#0000FF]GRUB_CMDLINE_LINUX=”reboot=efi”[/COLOR]but problem still exist. Of course I do > sudo update-grub after modify grub file.

Now after cat /proc/cmdline I get:
> BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic.efi.signed root=UUID=9313207e-d5c8-4233-901c-fe3bfc87f638 ro reboot-efi quiet splash i8042.reset i8042.nomux vt.handoff=7


On Xubuntu 13.10 there wasn't any problem with restart or shut-down. My PC: ASUS 1225B.

---

