---
title: "Command-line installation with custom GRUB placement"
date: 2013-11-13
forum: General Help
---

### Post by Laiquendi on 2013-11-13
Hey there!

Could you please help me, I want to intall Ubuntu by command-line mini installer (graphics doesn't work from full CD) and I want to place bootloader (GRUB) on the same partition (/dev/sdXY) as Ubuntu, NOT to overwrite MBR.
This is because I use TrueCrypt, and when I press [ESC] it looks for other bootloaders and should find GRUB.

I remember that in earlier versions there was that tick of checking where you want your GRUB, but I don't know how to achieve it while in command-line installation...

Thanks!

---

### Post by Allavona on 2013-11-13
run your grub config but do not install grub. You'll then have a grub.cfg file for the truecrypt bootloader to find.

---

### Post by Laiquendi on 2013-11-13
Thanks!

---

