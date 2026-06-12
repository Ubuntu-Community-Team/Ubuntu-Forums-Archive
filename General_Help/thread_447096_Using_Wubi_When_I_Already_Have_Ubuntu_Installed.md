---
title: "Using Wubi When I Already Have Ubuntu Installed?"
date: 2007-05-17
forum: General Help
---

### Post by kadath on 2007-05-17
I already have Ubuntu and Windows installed on their own partitions. My question is, is it possible to use Wubi to install Kubuntu on my Windows partition? I want to do this to try out pure Kubuntu as opposed to installing kubuntu-desktop on my regular Ubuntu install.

---

### Post by ago on 2007-05-17
yes

you'll need to boot into windows, and from there into kubuntu

---

### Post by tuxcantfly on 2007-05-17
or, you can boot Ubuntu and install using Lubi: [http://ubuntuforums.org/showthread.php?t=442597](http://ubuntuforums.org/showthread.php?t=442597) which will bring the same result, only the disk images will be on your linux partition, not the windows one, and it'll avoid some of the issues with Wubi (specifically the GRLDR bootloader which fails to boot on some systems), and for the bootloader, you'll boot from Ubuntu's GRUB not the Windows NTLDR

---

