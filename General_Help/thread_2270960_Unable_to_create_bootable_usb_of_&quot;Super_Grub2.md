---
title: "Unable to create bootable usb of &quot;Super Grub2 Disk&quot;"
date: 2015-03-26
forum: General Help
---

### Post by swarup on 2015-03-26
I've been trying to use the Startup Disk Creator to create a bootable usb of "Super Grub2 Disk" ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)), but I keep getting an error and cannot get the bootable usb made. I need to use the usb to boot into Ubuntu in a computer with a dual boot and grub is not working. If I can use this usb to boot into Ubuntu, then in a terminal window doing "sudo update-grub" should re-establish grub.

How have others created bootable usb of "Super Grub2 Disk"? Or is there another bootable software to use for getting booted once into Ubuntu?

---

### Post by yancek on 2015-03-26
Have you tried the method suggested on the SuperGrubDisk wiki, link below?

[http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)

---

### Post by swarup on 2015-03-26
Wow, I was searching and working on this for hours this morning but hadn't seen this wiki. 

One question:

To use the option "**Gnu/Linux (and being usable for storage later)**, it says:

> Format your pendrive as FAT32. However make sure to leave 3 MB unallocated at its beginning.

So I guess this could be done in gparted right? Just slide the left border of the partition to the right so that 3 mb are unallocated.

---

### Post by yancek on 2015-03-26
>  	 So I guess this could be done in gparted right? Just slide the  left border of the partition to the right so that 3 mb are unallocated. 		

Yes.

---

