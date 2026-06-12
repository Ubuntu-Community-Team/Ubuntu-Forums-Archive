---
title: "reboot problem"
date: 2007-04-22
forum: General Help
---

### Post by wubi newbie on 2007-04-22
hi everybody. once the installation of ubuntu is done, wubi asks me to reboot. but this is the msg i get when i choose ubuntu.

[img]http://img241.imageshack.us/img241/7408/23042007105sl2.jpg[/img]

i do have xp and vista already installed. on the first boot menu i can choose either xp, vista or ubuntu. and if i choose xp i also get another boot menu asking me if i wanna load xp or ubuntu.

i get the same error whether it's in the first or second boot menu.

thank you for helping me

---

### Post by Spegelius on 2007-04-23
I have that same problem when i have Vista bootloader active. It seems grub doesn't like Vista bootloader and refuses to use the boot partition. It doesn't matter that i have also Windows 2003 installed. My only solution for that was to remove Vista bootloader with Vistabootpro 3.1 (which does mean that i cannot boot to Vista before i reinstall Vista bootloader...).

You could try moving the Wubi folder to some other partition of your second disk, if it has enough space... dunno if grub can boot if that partition doesn't have boot recored.

---

