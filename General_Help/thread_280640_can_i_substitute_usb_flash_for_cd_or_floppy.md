---
title: "can i substitute usb flash for cd or floppy?"
date: 2006-10-19
forum: General Help
---

### Post by dfong63 on 2006-10-19
here's the scenario.  i have the ubuntu download on my HD.  the instructions say to burn it to a CD.  but, i would rather copy it to a USB flash drive and boot it from there.  is it possible to do this?

my computer's BIOS does *not* support booting from USB.  so in order to do this, i think i need to either
(a) somehow get grub to understand how to read the data from the USB flash drive; or
(b) boot into linux and somehow get linux to re-start using the data (including kernel) on the flash drive.

i do have linux already installed on the hard disk.  i am willing to put some files on the hard disk itself in order to facilitate booting from USB.  but i do not want to (for example) copy the kernel from the flash drive to the hard disk to boot it.  because, i want to be able to boot different distributions from the flash drive(s), without altering my hard disk.

in other words, i want to be able to use the flash drive like a CDROM drive.  the hangup is that unlike the CDROM drive, the BIOS does not know how to access the flash.  but linux knows how to access the flash.  so it seems to me that this should be possible.

i've done a lot of googling, but most of the pages i've found seem to assume either that
(a) the BIOS understands USB; or
(b) you want to boot the test installation via floppy or CDROM.

instead, what i really want is software that i can load (one time) on my hard disk, in order to make it possible to load different distributions (from time to time) via USB flash, for experimentation.

i'd appreciate the community's help with this question.

---

### Post by jpkotta on 2006-10-19
This is probably easier for testing: [https://help.ubuntu.com/community/VmwareServer](https://help.ubuntu.com/community/VmwareServer)

Also, [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by dfong63 on 2006-10-19
thanks for your response.

i'm not sure vmware will do what i want.  it sounds like a lot of trouble to setup.  also, i'm concerned about how much disk space this approach will consume.

as for the bootfromusb web page: i read it, but i found it somewhat confusing.  since my machine's BIOS does not directly support booting from USB, i interpret the web page to say that i need to burn a CD.  that is what i'm trying to avoid.  it's a hassle to have to burn a CD just to do a test.  and if i need to modify something in the distro, it's even more of a hassle.

if the CD or floppy is just an intermediate stage toward getting a system rooted on the USB flash, then is it possible to use a hard disk for that intermediate stage instead?

it seems to me that there just "should be" a way to do what i am asking.  grub supports booting; linux supports usb flash drives.  why shouldn't there be a way to combine these functionalities?

---

