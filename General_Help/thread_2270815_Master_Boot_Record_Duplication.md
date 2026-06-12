---
title: "Master Boot Record Duplication?"
date: 2015-03-25
forum: General Help
---

### Post by Joe_Ciaravino on 2015-03-25
I have Windows 7 as default boot, with Ubuntu, my BluRay Disk, and  memory card readers as boot devices. If I press F12 during boot, I see 2  identical Ubuntu entries as boot choices, and both of which work and  will boot into Ubuntu.

Here are two screen captures from Easy BCD. Pay particular attention to  entry 3 and 4, and tell me which one to delete in order to eliminate the  redundancy. What is "grub64" and "shim64"?

---

### Post by oldfred on 2015-03-25
Grubx64.efi is standard grub's UEFI boot and shimx64.efi is the secure boot version.
If you want the option to use secure boot you need shim, but then must also have the signed kernels and some other signed versions of grub.

If you are using UEFI, you should not need EasyBCD except perhaps for the fixes you may need to BCD with Windows.
UEFI is a boot manager or menu for boot choices. Grub is both a boot manager and boot loader for Ubuntu.
And EasyBCD modifies Windows BCD to be a boot manager for more than just standard Windows.

Or you have added another boot manager and that can add menu confusion.

And UEFI does not use MBR for booting. All systems share the efi partition and have separate folders for their own boot files.

---

### Post by Joe_Ciaravino on 2015-03-26
> **oldfred said:**
> Grubx64.efi is standard grub's UEFI boot and shimx64.efi is the secure boot version.
If you want the option to use secure boot you need shim, but then must also have the signed kernels and some other signed versions of grub.

If you are using UEFI, you should not need EasyBCD except perhaps for the fixes you may need to BCD with Windows.
UEFI is a boot manager or menu for boot choices. Grub is both a boot manager and boot loader for Ubuntu.
And EasyBCD modifies Windows BCD to be a boot manager for more than just standard Windows.

Or you have added another boot manager and that can add menu confusion.

And UEFI does not use MBR for booting. All systems share the efi partition and have separate folders for their own boot files.

I used Easy BCD so I could read the MBR. So the grub and shim entries stay as is. Do you have a suggestion on how to eliminate the second "ubuntu" entry from the boot menu that comes up with F12?

---

### Post by oldfred on 2015-03-26
Details are in the link in my signature.

With UEFI you can see all the boot files, just by looking at the efi partition and each folder for each system.
And Boot-Repair's Summary report gives a better idea of your configuration, generally worthwhile just to run to document your system.

Some systems will let you edit entries with your UEFI. Otherwise you have to manually remove files from efi partition. Best to back it up first, you should have a backup anyway.
And from Ubuntu or live installer booted in UEFI mode you can use efibootmgr to edit, update, delete or change UEFI boot entries.

If you do not delete an efi boot file from efi partition, UEFI will add it back.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Not sure now what EasyBCD has added or changed and whether that also needs updating or if it will auto sync after UEFI updates.

---

### Post by Joe_Ciaravino on 2015-03-30
> **oldfred said:**
> Details are in the link in my signature.

With UEFI you can see all the boot files, just by looking at the efi partition and each folder for each system.
And Boot-Repair's Summary report gives a better idea of your configuration, generally worthwhile just to run to document your system.

Some systems will let you edit entries with your UEFI. Otherwise you have to manually remove files from efi partition. Best to back it up first, you should have a backup anyway.
And from Ubuntu or live installer booted in UEFI mode you can use efibootmgr to edit, update, delete or change UEFI boot entries.

If you do not delete an efi boot file from efi partition, UEFI will add it back.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Not sure now what EasyBCD has added or changed and whether that also needs updating or if it will auto sync after UEFI updates.

oldfred:

Thanks for the advice. I ran Boot Repair from within ubuntu and deleted the redundant Ubuntu entry from within the Grub?, MBR?. That seems to have solved it. The second Ubuntu entry no longer appears when I press F12 during early boot (this brings up a boot menu of choices). 

The difference is that since then Windows bootloader is no longer in charge, and GRUB? is in charge. That is OK, as I now have additional choices, and can get  into safe Ubuntu boot, and memory check which I couldn't see before.

So, when I boot the computer and don't press any hot buttons, it first very quickly goes to the Ubuntu boot choice screen, and since I set the countdown timeout to ZERO, it flashes by very quickly. Then boots into Windows 7 as normal. If I want to get to the Ubuntu boot choice menu, I hit F12, then choose the (now) single Ubuntu entry, whereupon, I get to the Ubuntu boot choice menu screen.

All is well. Very cool. Thanks again!!

---

