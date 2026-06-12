---
title: "Convert ISO to IMG?"
date: 2007-09-22
forum: General Help
---

### Post by Githlar on 2007-09-22
In order to make a boot disk with Memdisk, I need to convert my ISO's to IMG's. I saw a newsgrou-style thread on another site that explained it, but I can't locate it anymore. Does anybody know how I can do this? I know it required dd and mkisofs, but beyond that i'm lost.

---

### Post by pPrdrm on 2007-09-22
Well, you could try **AcetoneISO2**.
I never used it my self but maybe it's what you are looking for:

**Features :**
- Mount / Unmount ISO, MDF, NRG, BIN, NRG (no password required)
- Display showing mounted images
- Automatic Mount, destination is not required
- Convert / Extract / Browse to ISO :
  *.bin *.mdf *.nrg [COLOR="Red"]*.img[/COLOR] *.daa *.cdi *.xbx *.b5i *.bwi *.pdi
- Play a DVD Movie Image inside Kaffeine / VLC with cover downloader
- Generate an ISO from a Folder or CD/DVD
- Generate / Check MD5 file of an image
- Encrypt / Decrypt an image
- Split / Merge image in X megabyte
- Compress with High Ratio an image in 7z format
- Rip a PSX cd to *.bin to make it work with epsxe/psx emulators
- Service-Menu support for Konqueror
- Restore a lost CUE file of *.bin *.img
- Blank CD/DVD
- Burn ISO / Cue to CD/DVD
- Mount Mac OS *.dmg images
- Retrieve INFORMATION of an image
- El-Torito support to create ISO bootable Cd
- Mount *.iso in a specified folder from the user
- Create a database of images
- Extract the Boot Image of a CD/DVD or ISO

Web site link:
[[COLOR="Red"]http://www.acetoneteam.org/central.html[/COLOR]]("http://www.acetoneteam.org/central.html")

Download link for Feisty:

[[COLOR="Red"]http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0.2-1~3v1ubuntu0_i386.deb[/COLOR]]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0.2-1~3v1ubuntu0_i386.deb")

---

### Post by bulletxt on 2007-09-22
If you need to extract a boot image from a cd or iso, then install AcetoneISO2 1.0.2

if you need to make a bootable iso do same thing ;)

be sure to not download xAcetoneISO2 as the website clearly states it has been stopped due to the new devolpment that will completely be inQT4 and not depend anymore on KDE

---

### Post by psusi on 2007-09-22
IMG has no standard meaning.  I do not know what memdisk is or what kind of file it wants, but if you are trying to build a bootable cd, you can't use an existing iso.  Typically you make a bootable floppy disk image and it gets built into the iso image for the cd such that the bios will emulate a floppy disk using that image.

---

### Post by Githlar on 2007-09-22
OK, so there is no standard to the IMG format. That's more disappointing than I thought. So, technically, I could just mount the ISO and use dd to create an IMG? But, then I'd lose the boot sector, correct?

Oh, and I don't have KDE, so I have to use the x version of that program.

---

### Post by psusi on 2007-09-23
No, if you read the cd image from the device, you are reading the iso, which does contain any bootable information it was built with.  What is it that you are trying to do here?

---

### Post by bulletxt on 2007-09-23
I think we are all together when saying we still didn't understand what are you trying to do :P

please explain exactly what is your need

---

### Post by muniak on 2008-06-15
Honestly I only half tried this backwards it seemed to work but I guess it's worth a try if you've run out of options? This is assuming you're talking about CloneCD's .img format?
[http://www.t2-project.org/packages/img2iso.html](http://www.t2-project.org/packages/img2iso.html)

---

