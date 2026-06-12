---
title: "Reinstalling Vista Bootloader from Linux?"
date: 2007-02-17
forum: General Help
---

### Post by Tauhshi on 2007-02-17
Is there any way to recover the Windows Vista bootloader from within Linux without the Vista DVD? I had installed Ubuntu, then deleted the partition, but it still boots with GRUB, but gives and error 17.

---

### Post by Dr. C on 2007-02-17
If I understand this correctly what is left of the Ubuntu installation is that portion of GRUB on the MBR. So GRUB has to be remouved from the MBR. I have fixed this in a dual boot system with XP by booting from a DOS floppy and using the command:

 fdisk /mbr

There must not be a space between the slash and mbr

---

### Post by Tauhshi on 2007-02-18
Well, I dont have a floppy drive. Also, when I try to boot into Vista, I get stuck on the loading screen. It just stays on that . . . forever . . .

---

