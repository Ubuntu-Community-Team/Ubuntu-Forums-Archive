---
title: "Any danger of reinstalling Windows 8 in dual-boot with Ubuntu 16.04?"
date: 2017-11-22
forum: General Help
---

### Post by smith73 on 2017-11-22
Are there any dangers of reinstalling Windows 8 while running dual-boot with Ubuntu Mate 16.04? As Windows sort of doesn't detect Ubuntu on the disk and I'll need to set uefi boot from cd in Boot Load Priority settings in Bios among 3 additional Ubuntu Boot options which have appeared after Ubuntu installation and eventually will change Boot Load priority. Will Ubuntu Grub loader return to previous boot sequence in Bios after Windows 8 re-installaion?
I installed Ubuntu in dual boot with Win8 automatically. Should I take the record of how many (mega)bytes it consumes and not set disk space in GB as previously? Maybe should I run something in Ubuntu before reinstalling Windows 8?



Thank you very much

---

### Post by #&amp;thj^% on 2017-11-22
Read the post by evgeny with 122 up-votes.
[https://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](https://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)
Sound Daunting but it is pretty straight forward if you read and fully understand.

---

### Post by oldfred on 2017-11-22
If BIOS Windows is known to not correctly rewrite partition table. It does not delete any actual data, but you have to refresh partition table with testdisk or parted rescue. Best to backup partition table with sfdisk first.

If UEFI, it does not damage partition table, but whether installing/updating Windows or Ubuntu, they will reset themselves to be default in boot order.
You will need to go into UEFI and reset boot order or boot Ubuntu live installer and use efibootmgr to reset boot order. You may be able to directly boot Ubuntu from UEFI boot menu.

But anytime you make any major system changes you must fully back up all your data and configurations, whether Windows or Ubuntu. And you should have those backups as normal procedure as hard drives to fail or users make errors and lose data.

---

