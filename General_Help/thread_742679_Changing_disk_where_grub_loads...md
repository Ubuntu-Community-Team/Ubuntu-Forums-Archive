---
title: "Changing disk where grub loads.."
date: 2008-04-01
forum: General Help
---

### Post by jprebechi on 2008-04-01
Hello people:

I've got 2 different disks with ubuntu (1 sata (sda), with /, /home, and swap, and 1 pata (hda), with a whole partition mounted in /storage, with more personal archives).

The thing is, that i have 2 different problems;
1- if i disconnect the hda disk, ubuntu doesn't load (it asks for the system disk, wich is, actually, the connected one).
2- if i start with the live cd, in g/qt parted, i have to have both disks connected, otherwise, only one connected won't be recognized..

now, i'm installing kubuntu, and in the last install part, i clicked advanced.. and the grub was configured to be installed in hda0 (while i installed my /, /home, and swap partitions in the sda disk).

so, is that the problem? when i install again (i'm planning to do it in less than 2 months :P) should i change the partition/disk where i want to install the grub?.

it's the only thing i can think that can be causing these 2 problems...

Thx in advance.

jprebechi.-

---

### Post by fsmithred on 2008-04-04
Grub (or some boot loader)  should be in the MBR of the first disk. It looks like your motherboard wants to call the IDE drive the first drive when it's connected, and it finds grub there. When you disconnect it, the sata drive is the first drive, and your boot loader is on the disconnected drive. You could install grub to the mbr of the sata drive, but I think you'll need to change some grub settings, and if you reconnect the ide drive, you'd need to change them back. 

Better to stick with one hardware configuration if you can. If you really have to be able to pull hda out repeatedly, there might be another solution, such as booting from floppy/usb/cdrom and making menu entries for each configuration. Or your bios might allow you to choose which drive is first - then you could tell it to make sda first and leave it that way, with grub on sda instead of hda..

---

