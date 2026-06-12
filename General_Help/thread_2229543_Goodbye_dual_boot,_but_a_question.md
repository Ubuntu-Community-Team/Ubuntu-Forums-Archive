---
title: "Goodbye dual boot, but a question"
date: 2014-06-13
forum: General Help
---

### Post by oldrocker99 on 2014-06-13
Long since Windows 7 quit behaving for me, and has a frozen mouse pointer and can't see a keyboard, I want to delete everything but the Users folder, and use the entire partition for storage. I have /home on a separate drive. If I delete everything but the Users folder and run update-grub, will that be enough?

---

### Post by oldrocker99 on 2014-06-14
Oh, well. I did just delete everything, ran update-grub. I still see Windows in the GRUB menu, but it's gone!

---

### Post by kurt18947 on 2014-06-14
Just guessing here.  I wonder what would happen if you ran update-grub from a live CD/USB?  If I'm reading correctly and you deleted Windows, it's certainly not going to boot.  Why not just backup or move the Windows data files and delete everything?

---

### Post by oldfred on 2014-06-14
Did you delete the hidden in Windows 100MB boot partition? That has the boot files which is what grub usually finds.
Post this:
sudo parted -l

---

### Post by kurt18947 on 2014-06-17
> **oldfred said:**
> Did you delete the hidden in Windows 100MB boot partition? That has the boot files which is what grub usually finds.
Post this:
sudo parted -l

When did Windows start creating a 100 MB boot partition on non-UEFI  MSDOS partitioned machines?  I did a temporary Win 7 install using a DVD burned from a recently downloaded iso and there it was, a 'system' partition.  Earlier Win 7 installs didn't do this.

---

### Post by oldfred on 2014-06-17
Windows 7 only installs to one NTFS partition when you manually install to a already created NTFS partition with the boot flag. 
All standard Windows 7 & 8 systems as purchased system or installed to a blank drive in BIOS boot mode use MBR partitions and create a separate 100MB boot partition. That was so you could encrypt main install as boot files cannot be encrypted and boot partition has its recovery or really the repair console.

Many newer systems were UEFI capable but Windows 7 was in stalled in BIOS boot mode.

---

