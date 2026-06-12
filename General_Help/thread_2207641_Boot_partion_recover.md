---
title: "Boot partion recover"
date: 2014-02-24
forum: General Help
---

### Post by haskell2 on 2014-02-24
I did install ubuntu side by side wind 8. But lost access to wind 8. My objective is recover access to the wind partition  or to wind recover partition to reset as did come from factory.

use boot-recover to get some info: [http://paste.ubuntu.com/6990547/](http://paste.ubuntu.com/6990547/)

Thank's

---

### Post by oldfred on 2014-02-24
You have Windows in UEFI boot mode. It looks like you originally had Ubuntu in BIOS boot mode, but Boot-Repair converted you to UEFI.
But it also looks like Boot-Repair offered the 'buggy' UEFI fix. That is for some systems that have modified UEFI to only boot Windows. So it renames shim to have Windows file name. But then booting Windows from UEFI actually boots Windows and you can only boot the backed up renamed bkpbootmgfw.efi Windows efi file from grub not from UEFI.
If you can boot ubuntu entry in UEFI, undo the rename, so you can directly boot Windows from UEFI menu.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by haskell2 on 2014-02-24
So i should change to UEFI and then apply Boot-repair with restore EFI backups?

---

### Post by oldfred on 2014-02-24
Yes.
Since you have Windows in UEFI boot mode, everything you do should be in UEFI boot mode. No reason to go to BIOS unless you have one of the few systems that will not boot anything but Windows in UEFI mode.

---

