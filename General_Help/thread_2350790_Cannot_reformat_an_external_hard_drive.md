---
title: "Cannot reformat an external hard drive"
date: 2017-01-27
forum: General Help
---

### Post by PjJns on 2017-01-27
Hi community,
I cannot reformat an external hard drive after accidently choosing it as the wrong drive for boot loader.  Tried all posts I saw.  Please help.

Any info greatly appreciated.

---

### Post by oldfred on 2017-01-27
Was it just boot loader or the Ubuntu installer using dd.
The dd install option puts misc data into the location on the drive where partition table info should be, so most tools see corruption.

Make absolutely certain that you use correct drive for sdX. It may change when you plug in an external drive.
sudo parted -l
       Zero out MBR and partition table
dd if=/dev/zero of=/dev/sdX bs=512 count=1

---

### Post by ajgreeny on 2017-01-28
If you prefer a GUI application use gparted from a live Ubuntu USB and go to the **Device** menu, choose the USB, and then **Create new partition table**.

That will wipe everything on the USB and allow you to start again.

---

