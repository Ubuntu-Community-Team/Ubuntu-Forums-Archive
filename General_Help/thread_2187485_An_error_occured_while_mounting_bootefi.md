---
title: "An error occured while mounting /boot/efi"
date: 2013-11-12
forum: General Help
---

### Post by overcome2 on 2013-11-12
[COLOR=#333333][FONT=UbuntuRegular]I seem to have damaged something during the upgrade from 13.04 to 13.10.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I get this error when loading Ubuntu:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**An error occured while mounting /boot/efi**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**Press S to skip mounting or M for manual recovery**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried running boot-repair from the Live CD, here is the summary file:[http://paste.ubuntu.com/6405180/](http://paste.ubuntu.com/6405180/)[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-12
Bit difficult to tell.
 It looks like you originally installed wubi. But wubi does not work with gpt partitioned drives or any system pre-installed UEFI secure boot Windows 8.
It then looks like you installed in BIOS boot mode not UEFI boot mode. If then you used Boot-Repair to convert to UEFI, it may have left an old setting in grub to reinstall in BIOS mode on major updates.

But it looks like Boot-Repair ran again and you have a UEFI install. If after a couple of reboots it still does not work I would run chkdsk from Windows on efi partition.
Or (note that it must be unmounted, best from Live installer.)
 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sda2

You can follow these Windows fixes to mount efi partition but also run chkdsk on the efi partition.

 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)



Then use Boot-Repair again in UEFI mode and possibly fully uninstall/purge grub2 and reinstall grub2.

---

