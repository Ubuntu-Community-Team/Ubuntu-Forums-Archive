---
title: "Netinstall?"
date: 2004-11-15
forum: General Help
---

### Post by Swad on 2004-11-15
A brief browsing of a few documents didn't get me the answer I wanted.  Is there a netinstall cd / floppies?  If not, are there future plans?

---

### Post by jdong on 2004-11-15
Unfortunately, there's no netinstall option, short of manual debootstrap...

Search debootstrap on the forums and the Wiki. I'm SURE I saw it somewhere.

---

### Post by duff on 2004-11-15
[QUOTE=Swad]A brief browsing of a few documents didn't get me the answer I wanted.  Is there a netinstall cd / floppies?  If not, are there future plans?[/QUOTE]
Not sure of the point of a Ubuntu netinstall, unless you're going to install hoary.  Everything you need to get warty started is on the CD.  It's not like debian where there's several routes to take: server, desktop, etc.  It's just GNOME.

---

### Post by FLeiXiuS on 2004-11-15
The CD is pefect, it'll be faster and much more reliable.  I may suggest just burning an ISO.  If a burner is unavailable hook up a spare pc and run a network install. (http/ftp)  Of couse you will need some sort of kernel loading problem (linux) on a boot sector.  


My Method Short and Sweet
-Extract Ubuntu ISO
-Copy initrd/kernel.img over to a /boot partition on the PC where installation will take palce
-Edit grub / lilo to boot the kernel you just copied over
-Boot the installation kernel
-Configure for network install
-voila!  \\:D/

---

### Post by jalrnc on 2004-11-16
Well, the CD may be perfect but the only way I was able to install Warty was through the network... the CD (and also the live CD) kept hanging on my system (PII 400Mhz, I can provide more details if anyone is interested). Hardware detection maybe? Not sure what those CD images are doing differently, but I grabbed this image from the Ubuntu archive, burned it on a CD, and the installation went perfectly fine:

[http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-i386/release/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/warty/main/installer-i386/release/images/netboot/)

João

---

### Post by GaibryelRemorse on 2004-12-07
Hello, currently I'm having issues with a ThinkPad refurbished 380XD.
For some reason, the computer will not boot ISOLinux, and thereby I can't just sure the regular install CD. In addition, the floppy drive is surely dead.

A friend of mine and I are trying to get this machine to at least get a minimum install and then dumping another laptop's dpkg list to do the full install of Ubuntu.

However, the main issue we're running into at the present time is getting GRUB installed/configured correctly to follow your instructions in netinstalling.

Help? In either step-by-steps or just in getting GRUB to boot

Thanks,
Gaibryel

[QUOTE=FLeiXiuS]The CD is pefect, it'll be faster and much more reliable.  I may suggest just burning an ISO.  If a burner is unavailable hook up a spare pc and run a network install. (http/ftp)  Of couse you will need some sort of kernel loading problem (linux) on a boot sector.  


My Method Short and Sweet
-Extract Ubuntu ISO
-Copy initrd/kernel.img over to a /boot partition on the PC where installation will take palce
-Edit grub / lilo to boot the kernel you just copied over
-Boot the installation kernel
-Configure for network install
-voila!  \\:D/[/QUOTE]

---

