---
title: "Computer fails to boot after deleting Windows and reinstalling Ubuntu-Asus"
date: 2018-08-22
forum: General Help
---

### Post by alexvasilikop on 2018-08-22
Today i opened my computer and instead of booting into gnu grub it  directly booted in the BIOS. The pc had ubuntu and windows alongside  ubuntu installed.Not knowing what to do I decided to reinstall only  ubuntu so during the installation i deleted all old partitions and  installed only ubuntu from a live usb. The problem is not solved. I  tried to use boot-info and this is the report i got: [http://paste.ubuntu.com/p/jHSmD34rRv/](http://paste.ubuntu.com/p/jHSmD34rRv/).

  I am using ASUS F554L
  Any help would be much appreciated thanks.

---

### Post by ajgreeny on 2018-08-22
I think your problem is summed up in the last but one part of the Boot-Info report
> =================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?
If you boot the install medium on the USB in UEFI mode and accept the default install it will automatically create all the necessary partitions, hopefully solving your problem.

---

### Post by TheFu on 2018-08-22
Welcome to the forums.  

Well, you've definitely wiped Windows, that is certain.  I'm guessing, but if Windows did an update, it could have overwritten the boot areas, which they commonly do.  To correct it, isn't hard, but booting off an Ubuntu flash drive, going into rescue mode and telling it to reinstall grub would have been the method I tried first. This is a good skill to have even with out Windows.

Someone else will probably need to reply to be 100% accurate, but looking at the boot-info, you have a GPT disk, but installed Ubuntu like it was a BIOS, not UEFI, installation. Was that intentional?  Is your BIOS set to boot in UEFI mode or Legacy BIOS mode?  That would be the first thing I checked.

There are other people who have performed a similar installation here, and we've helped them out, but it is probably fastest if you search for those threads to find the advice given.

---

