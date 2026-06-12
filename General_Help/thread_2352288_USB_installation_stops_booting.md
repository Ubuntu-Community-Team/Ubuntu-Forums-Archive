---
title: "USB installation stops booting"
date: 2017-02-11
forum: General Help
---

### Post by daim.willemse on 2017-02-11
Hello all!

I have made an install of 16.10 on modern hardware laptop, using the usb stick and an external usb 3.0 disk (harddrive).
To install I have made three partitions:
EFI partion of 300 MB
Ext4 on /
SWAP

The boot stuff is installed on the EFI partition.

After the install I can boot the computer from this disk. 
However after one or two boots, the laptop will no longer boot from the usb drive.
I have looked in the bios. It recognizes that there is an UEFI type drive attached. The light on the drive shows the bios is looking.
However, when I tell the bios to boot from the usb drive, it skips to the next option.

What puzzles me most, is that this install boots one or two times and after that stops coming up.

Hopefully anyone has experience with this.

Kind regards,
Daim

---

### Post by daim.willemse on 2017-02-11
Additional information:
The bios allows to boot from a file.
When I point it to EFI/ubuntu/grub64.efi it boots just fine.
It seems that the bios is not finding this efi file by itself. 
What changes after first and later boots.
Daim

---

