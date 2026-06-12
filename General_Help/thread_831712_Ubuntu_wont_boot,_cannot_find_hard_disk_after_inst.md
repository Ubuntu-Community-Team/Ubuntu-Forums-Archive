---
title: "Ubuntu wont boot, cannot find hard disk after install"
date: 2008-06-17
forum: General Help
---

### Post by Mr-Heier on 2008-06-17
Hello.
I have tried to install Ubuntu to two different hard disk. One sata and one ide disk. Both give the same problem.

After i have installed Ubuntu to them they wont boot. It just says no boot disk when starting up the computer.

When installing Ubuntu it finds the harddisks and it looks fine.

The bios will not find the sata disk but Ubuntu install did. The Ide disk was both found by the bios and ubuntu.

What do i do?

Marius

---

### Post by Tomatz on 2008-06-17
> **Mr-Heier said:**
> Hello.
I have tried to install Ubuntu to two different hard disk. One sata and one ide disk. Both give the same problem.

After i have installed Ubuntu to them they wont boot. It just says no boot disk when starting up the computer.

When installing Ubuntu it finds the harddisks and it looks fine.

The bios will not find the sata disk but Ubuntu install did. The Ide disk was both found by the bios and ubuntu.

What do i do?

Marius

Did the ubuntu bootloader (grub) boot? 

I.e. you saw the grub bootloader menu but when you selected ubuntu to boot. The error occurred. or did it go straight to the error?

---

### Post by Mr-Heier on 2008-06-17
> **Tomatz said:**
> Did the ubuntu bootloader (grub) boot? 

I.e. you saw the grub bootloader menu but when you selected ubuntu to boot. The error occurred. or did it go straight to the error?

No the bootloader didnt boot. Straight to error, as if the hard drive was unplugged.

---

### Post by Tomatz on 2008-06-17
Is the drive set to primary drive in the bios?

That may be your problem.

---

### Post by Mr-Heier on 2008-06-17
> **Tomatz said:**
> Is the drive set to primary drive in the bios?

That may be your problem.

Yes it is. Its second boot device after the floppy. And Hard Disk boot priority is also set right.

If that was what you ment.

---

### Post by Tomatz on 2008-06-17
Sometimes grub (the bootloader) can end up being installed on the wrong disc/partition. Try setting each drive, in turn to primary and booting with them.

Hopefully grub is just on a different drive to ubuntu ;)

---

### Post by Tomatz on 2008-06-17
Any luck?

---

