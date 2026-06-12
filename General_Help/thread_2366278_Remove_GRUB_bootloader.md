---
title: "Remove GRUB bootloader"
date: 2017-07-15
forum: General Help
---

### Post by morbuscordis on 2017-07-15
How would I go about uninstalling the GRUB bootloader from an HP OMEN ax-203na?
The only OS on the hard drive is Windows 10 Home Edition. The problem occurred when attempting to install Ubuntu to a USB stick. I installed GRUB bootloader alongside Windows Bootloader. The laptop by default boots into Windows bootloader, however, GRUB still shows in the BIOS under boot manager.
How can I remove It?
I've tried automatic boot repair from firmware.
Thanks.

---

### Post by yancek on 2017-07-15
Since the only OS you have is windows, the microsoft site at the link below would be a good place to try.

[https://answers.microsoft.com/en-us/windows/forum/windows_8-desktop/edit-uefi-partition-how-to-remove-ubuntu-folder/1718f140-7b06-4046-b449-3065b260be30](https://answers.microsoft.com/en-us/windows/forum/windows_8-desktop/edit-uefi-partition-how-to-remove-ubuntu-folder/1718f140-7b06-4046-b449-3065b260be30)

---

### Post by oldfred on 2017-07-15
See one or two of these.
You need to remove the entry in the UEFI using efibootmgr and the /EFI/ubuntu folder in the ESP - efi system partition.

 UEFI How To Remove Ubuntu From A Computer Dual Booting With Windows 10 (UEFI only)
How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720?noredirect=1#comment1369050_497720)

---

