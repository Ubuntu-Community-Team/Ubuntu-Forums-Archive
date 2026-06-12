---
title: "Change GRUB2 default boot order."
date: 2013-11-13
forum: General Help
---

### Post by jake.cooper.94 on 2013-11-13
Old laptop, dual booting with Win 7 x86 and XBMCbuntu. Former for when the family want to access emails, the latter for my media TV. Obviously I want Win7 to boot by default, lest the family get stuck with XBMC while trying to access hotmail.
Now I know there's literally hundreds of guides on how to change the GRUB2 boot order, but the problem is that XBMCbuntu has no desktop as such. I've tried CTRL+ALT+F1 to get me to terminal, but there's not text editors available from there. I even tried booting a fresh version of Ubuntu from .iso. This way I get access to a desktop, and can access the GRUB files through the partition where they're stored, and can edit them fine, but I get a "can't find /cow" error when I try to "sudo update-grub"

Very much an amatuer at terminal and would appreciate pointers at what I'm doing wrong.

---

### Post by grahammechanical on 2013-11-13
This is what I think is happening. When you run update-grub it tries to update the grub configuration files on the ISO image. Hence, the error message. Trying running the command from an XBMC terminal.

You may also need to run its companion command

```
sudo grub-install /dev/sda
```

Do you have more than one hard disk? If so, then you may need to change sda to sdb if XBMC is on the second hard disk. By the way standard Ubuntu has a text editor called nano installed by default. XBMC may also have it installed.

Regards.

---

### Post by jake.cooper.94 on 2013-11-13
I thought I was on the right track. I figured the grub-install command worked locally, so I tried to cd to the XBMC partition, still didn't work. Didn't realise that is achieved with a suffix command. I'll try this when I get home and keep you posted.


[EDIT] You sir are a genius. XBCMbuntu has nano functionality right from terminal. So easy now I know how. No stuffing around with bootable builds.

Many thanks!

---

### Post by jake.cooper.94 on 2013-11-13
You sir are a genius. XBCMbuntu has nano functionality right from terminal. So easy now I know how. No stuffing around with bootable builds.

Many thanks!

---

