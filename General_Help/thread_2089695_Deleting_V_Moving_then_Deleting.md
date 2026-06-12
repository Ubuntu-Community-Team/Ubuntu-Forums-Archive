---
title: "Deleting V Moving then Deleting"
date: 2012-11-30
forum: General Help
---

### Post by TopEnder on 2012-11-30
G'Day All and Thanks in Advance.
In all OS (particular Windows), when a file is deleted, I am under the impression that the file is marked as deleted but not removed from the PC just a flag is set for that file, (the file remains and can be recovered if required).   If I move the file to a USB stick then delete that file is there any record of the file (left) on the PC.  Thanks TopEnder

---

### Post by dino99 on 2012-11-30
files are found into /var/cache/apt/archives. If they are not there and not installed, then you need to redownload them for new installation. Its done via the /etc/apt/sources.list.

---

### Post by howefield on 2012-11-30
> **TopEnder said:**
> In all OS (particular Windows), when a file is deleted, I am under the impression that the file is marked as deleted but not removed from the PC just a flag is set for that file, (the file remains and can be recovered if required).   If I move the file to a USB stick then delete that file is there any record of the file (left) on the PC.  Thanks TopEnder

Your understanding is correct. Deleting a file marks the space as available for new data to be placed over it but doesn't actually "clean" the space that the old file occupied. That's the case whether you move or copy.

---

### Post by Impavidus on 2012-11-30
> **TopEnder said:**
> G'Day All and Thanks in Advance.
In all OS (particular Windows), when a file is deleted, I am under the impression that the file is marked as deleted but not removed from the PC just a flag is set for that file, (the file remains and can be recovered if required).   If I move the file to a USB stick then delete that file is there any record of the file (left) on the PC.  Thanks TopEnder
If you're referring to trash, yes, Ubuntu moves deleted files to a hidden directory named .trash (or .Trash, I'm not sure) (at least, when deleting using the GUI). When you delete a file on a usb stick a .trash directory is created on the usb stick. And I think moving something to a usb stick defaults to copying, but you can override all those defaults and permanently delete stuff at once.

---

