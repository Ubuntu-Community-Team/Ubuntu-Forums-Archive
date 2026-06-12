---
title: "Grub Menu not updating Kernel List"
date: 2007-07-12
forum: General Help
---

### Post by gazzar on 2007-07-12
After installing a  low-latency kernel just recently, it dosent appear on the boot menu for GRUB (hitting ESC on boot). But if i cat /boot/grub/menu.lst, the low-latency menu items are included. Is grub getting its menu from somewhere else that i am not aware of. I only have 3  parttitions. sda1 (/boot), sda2(/) and sda3(swap). I dont have windows or any other OS installed. my install was done from a LiveCD onto a clean disk.

I have tried deleting entries in the menu.lst file, and they still appear on the menu when i reboot. But if i then cat the menu.lst file, they are still deleted.  update-grub, regenerates the menu.lst file as expected, populating it with all kernel images located in /boot, (which includes low-latency) but the bootup menu still remains the same with no sign ogf the low-latency kernel. 

Am i missing something, any help would be much apprieciated.

---

### Post by coffeecat on 2007-07-13
> **gazzar said:**
> I have tried deleting entries in the menu.lst file, and they still appear on the menu when i reboot.

There is only one explanation I can think of - there must be two versions of menu.lst on your hard drive, one you are editing and one which is being read by grub.

I'm wondering if you have a complete /boot directory with all contents written in your / partition, rather than /boot symlinking to your /boot partition - if you follow me. :? I can't quite work out which of these grub would be reading or how the installer could have set things up like this.

I'm not quite sure how I would go about 'looking' at the two menu.lst files (if there are indeed two). Perhaps booting up with a live CD and mounting both /boot and / separately? A look in fstab might clarify things a little. Is /boot separately mounted from / ?

If my hunch is right, I wonder where the system has put your new low-latency kernel.

---

### Post by undecidable on 2007-07-13
It is possible to have two boot loaders installed in a single boot setup: one in the MBR and one in the partition.  I have a boot loader (xosl) in the MBR which then boots to grub in the partition which then boots to my kernel.  It is of course possible to do the same with grub in the MBR (though I haven't done it, though I have booted from grub on a floppy to grub on the partition).   

The install proces asks you where you want your grub - partition or mbr, and if you have done multiple installs, you may have one of each, and the one in the mbr may or may not point to the one in the partition, and if not will just point to the bootable kernels directly.

Where each will put its menu.lst I do not know (clearly there cannot be 2 /boot/grub/menu.lst) but obviously you can do a search for it.   

If the above is actually the problem, then the answer (where the 2nd menu.lst) is would certainly be interesting.

---

### Post by gazzar on 2007-07-23
Thanx for the replies, i gained enough info from them to find and fix the problem.

It seems it was the result of having installed over a previous install without the same grub options and this left me with a /boot partition and a /boot directory in /.

grub was using the /boot dirextory  in / to boot from but then the /boot partition was being mounted over it and any further updates or editing was being done on that directory. hence, any manual editing of menu.lst was not being used on bootup.

I fixed the problem in the following way.

on the grub boot menu, i entered into the command line
i set the root partition for grub to use, (noting grub uses hd and not sd for sata drives)

grub > root (hd0,0)

i then  setup grub on the  MBR of my first disk drive

grub>  setup (hd0)

then as the menu.lst file in the /boot partition was from a previous install, i needed to alter all of the UUID references in the menu entries to point to my / partitions UUID. This i got by using the blkid command in a shell after booting from the livecd. i then used the UUID of/ ( sda1) partition for all the menu.lst entries.

worked a treat

I hope this info is helpful to anyone else with this problem.

---

