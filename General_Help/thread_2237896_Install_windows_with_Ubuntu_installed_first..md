---
title: "Install windows with Ubuntu installed first."
date: 2014-08-04
forum: General Help
---

### Post by Garchomps on 2014-08-04
I have Ubuntu installed on my laptop but I would like to install Windows for games. Is there anyway I can go about this without removing the Ubuntu installation? It is encrypted btw.

---

### Post by Bucky Ball on 2014-08-04
No idea about whether encryption will make any difference, but the way I've done it in the past is to install Windows then boot from a Live disk/USB and install and run Boot Repair. Has always worked to fix things for me.

Use BR:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

---

### Post by oldfred on 2014-08-04
If it is encrypted, is it just the /home or the full drive with LVM?
I do not know LVM, but you have to use LVM tools to shink the LVM and then shink the partition to make space.

If BIOS you should still have a primary partiiton as Windows will only install to a primary partition formatted NTFS with the boot flag.
Not sure if UEFI.

---

### Post by Rob Sayer on 2014-08-05
I'd do what what was suggested in post #2.  Windows does not understand Linux file systems like the ext4 ubuntu default.  It thinks it's all unallocated space.  When installing it it'll overwrite it, and I found in Windows that you can tell it to do something and it'll still do it the way it wants to sometimes.

---

### Post by john_burns2 on 2014-08-05
AFAIK, First thing Windows does is to format the HDD,(irrespective of partitions created on the HDD) then install itself. (designed to do this) The only way to dual boot is to install Windows, then re-install Ubuntu alongside Windows.

---

