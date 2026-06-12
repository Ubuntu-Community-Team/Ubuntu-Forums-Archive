---
title: "Old Gateway Desktop install problems"
date: 2008-02-08
forum: General Help
---

### Post by patmalcolm91 on 2008-02-08
My friends computer recently kicked the bucket, and he wants me to install ubuntu on it to get it back into shape. The computer is a LP Mini-tower TB3 Essential 500 with BIOS version: 4W4SB0X0.15A.0017.P12 . It used to run Win98. When i reboot the computer with the install cd in the drive, it doesn't seem to even recognize the CD, but instead brings up a "Gateway Recovery CD" screen, which i've discovered, is the file C:/autoexec.bat. It asks me to put in the Windows Backup CD and press F1, or press F10 to exit to DOS-Prompt.

Doing some playing around, it seems that in C:/CDROM there are files that appear to be from the Gateway Restore CD. I tried (backing them up first) deleting them, deleting the directory and remaking it, but that did nothing. I have the BIOS set to boot CD first.

Is this possibly a problem with the CD Drive itself? I do have a spare drive sitting around i could try, but want confirmation that this might work first as this isn't my own computer. Or is this something with the BIOS version? Has anyone else had success with this computer?

I've tried botting the Gutsy LiveCD, Gutsy Alternate CD, and a PCLinuxOS CD. none to any avail.

Thank you in advance for any help! I have to work tomorrow, so i won't be able to respond until late tomorrow night, but please, any help or a point in the right direction will be greatly appreciated!!!

Thanks in advance for any help

---

### Post by Pelham123 on 2008-02-08
Couple of things...

Can you disable the second/third boot options, do you're left with only boot from CDROM?

Do you have floppy drive? I found this on the the 7.10 install CD :) (under install/README.sbm)

[I]About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.
[/I]

Good luck


Jeez...gotta love old computers ;)

---

### Post by patmalcolm91 on 2008-02-08
Wow, thanks for all the info, I'm gonna try this tonight when i get home. I'll let you know how it goes.

No, I can't remove any boot devices, only move them up or down the list.

---

### Post by patmalcolm91 on 2008-02-09
I just made the SBM floppy and booted it, it worked great, but in the boot menu there, it shows the CD Drive as empty. Does anyone have any more suggestions where to go from here? BTW, thank you Pelham123. Tomorrow I'm going to try to replace the CD drive and see what happens.

---

### Post by patmalcolm91 on 2008-02-10
turns out it was just the CD drive. thanks for the SBM info though, i'll be keeping that floppy disk handy for the future.

---

