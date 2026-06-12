---
title: "Can't boot any linux from usb flash drive (black screen = monitor turns off)"
date: 2014-04-08
forum: General Help
---

### Post by 7h364m3 on 2014-04-08
Hello, 
I've got a problem.
I made my bootable usb flash drive with Universal USB Installer.I've put there Ubuntu 12.04.4 -64 bit.
There problem is when i boot it, it show's me the ubuntu background with some strange icon, then my monitor turns off.
I got the same problem when i tried with Kali linux when finished with loading my monitor turns off.
The problem is not in the usb, cuz i tried it on another pc and it works.
But on my home pc it won't work.

---

### Post by oldfred on 2014-04-08
Do you have a nVidia chip or video card. I have nVidia and if I do not use nomodeset I get exactly that until I install nVidia drivers after install. It works differently on installer boot and first boot after install.

If BIOS from installer, hit any key while tiny accessiblity icons are at bottom of screen then f6 to add nomodeset.
       At grub menu after install, you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

