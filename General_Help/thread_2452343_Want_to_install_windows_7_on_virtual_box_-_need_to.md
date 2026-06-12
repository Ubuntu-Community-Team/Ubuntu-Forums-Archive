---
title: "Want to install windows 7 on virtual box - need to create ISO file?"
date: 2020-10-20
forum: General Help
---

### Post by DVD-R on 2020-10-20
Hello,
I would like to experiment installing Windows 7 into virtual box.
I have a windows 7 install disk - so perhaps that is the easiest approach?
Or I could perhaps convert the windows install disk into an ISO?

However, I'm curious about how to use Ubuntu to create the ISO file from the windows install disk anyway.
So the last question is - does anyone have a recommended application for doing that?

Thanks in advance!

---

### Post by deadflowr on 2020-10-20
> I have a windows 7 install disk - so perhaps that is the easiest approach?
Yes, it is.

While I'm sure  most burners apps like brasero and k3b can do what you want, you already have the image,
and virtualbox can handle dvd/cds fine, so i don't see the need to create an image for it.

---

### Post by oldfred on 2020-10-20
UEFI or BIOS?
Original Windows 7 DVD was BIOS only & had to be copied to flash drive and some files moved around to create the /EFI/bootx64.efi file for UEFI boot.
Update to newer Windows 7 included that folder & files for UEFI boot.

---

### Post by DVD-R on 2020-10-20
Thank you!
Files on the disk are dated for 2011, and there is a file on the disk named "bootmgr.efi"

So I'm not sure if it is EUFI or BIOS
But I have a suspicion that its EUFI

Is there a way I can confirm that?

---

### Post by oldfred on 2020-10-20
For UEFI boot on external flash drive the path must be /EFI/Boot/bootx64.efi.
For Windows bootx64.efi would be a copy of  bootmgfw.efi. For Ubuntu it is a copy of shimx64.efi.

Bootmgr is normally for BIOS boot, but not sure what bootmgr.efi is?

Default install of BIOS Windows uses a separate NTFS primary Boot partition with boot flag. First two files are in that boot partition.
Vista,  win7 and newer Windows in BIOS boot mode
  Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives.
Windows only installs in UEFI boot mode to gpt partitioned drives.

---

### Post by SeijiSensei on 2020-10-20
I'm with deadflowr. Just put the DVD in the tray, hit New in the VirtualBox management application, and tell the installer to use the DVD.

---

### Post by DVD-R on 2020-10-20
Thanks very much everyone!
I think I will go for the install in VB and see what happens!  :-]

My thanks

---

