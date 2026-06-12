---
title: "tempermental usb thumb drive"
date: 2007-08-18
forum: General Help
---

### Post by paradoxni on 2007-08-18
Im having issues with a usb thumb drive, it only appears when i leave it plugged in during boot.. if i unmount/remove it and then reinsert - or - boot the system first and then plug it in - it does not appear... I have to reboot the entire system to get it to appear again.

Ubuntu is set to auto detect usb drives and when i plug other drives/ memory cards  in they are detected fine, it is just this one thumb drive.

---

### Post by gobbles414 on 2007-08-19
Hey paradoxni,

EDIT: If your thumb drive has one of those hidden partitions on it -- such as those used by U3 Smart Software -- go to the manufacturer's website and get instructions on how to delete the hidden partition. Many manufacturers will make you use Windows or a Mac for this removal.

The easiest fix may be use a Windows computer to reformat the thumb drive as a FAT volume (**not** as a FAT32).

Alternatively, if you don't mind losing the data on your thumb drive, download the Gnome Partition Editor from the Synaptic Package Manager. Then use the partition editor to reformat your thumb drive to FAT.

---

