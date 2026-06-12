---
title: "Making a bootable floppy for BIOS flash"
date: 2008-05-21
forum: General Help
---

### Post by malfist on 2008-05-21
I need to follow the instructions here: [http://www.machspeed.com/tech/biosupdate2.html](http://www.machspeed.com/tech/biosupdate2.html) to flash my bios. I have the two files needed, but I don't know how to make it bootable, I've already rebooted with just those two files on the floppy and that didn't work.

---

### Post by fsmithred on 2008-05-22
You have a few options:

-Copy the files to an old win98 or dos boot disk

-Make a boot floppy on a windows machine with "format /s a:"

-Download a boot floppy image from somewhere and use dd to copy it to the floppy (something like "dd if=some_boot_floppy_image of=/dev/fd0")

-Get a motherboard that has a flash utility built into the bios, so you can put the file on an ordinary usb stick.

---

### Post by malfist on 2008-05-22
I finally figured out how to boot into my windows partition (the reason I want the update) and made the boot floppy.* My motherboards AGP slot is flaky and the motherboard's USB will quit working randomly (the PCI usb card still works) but the 'update' was the exact same version I had from over two years ago. Looks like I need a new motherboard.

*keyboard and mouse are usb, motherboard always kills it's usb on boot into windows and most of the time on linux (although it will come back on after the login screen has been up for a few seconds)

edit: FreeDOS would have worked if I'd known how to use the flash program. (The flash program needed absolute path to the new bios, not a relative one)

---

