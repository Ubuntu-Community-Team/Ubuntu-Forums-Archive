---
title: "Grub restore in Dell Desktops"
date: 2006-11-02
forum: General Help
---

### Post by repager on 2006-11-02
Having just tried to use the Super Grub Disk(SGD)to restore an MBR overwritten by WinXP- and failed! All low tech alternatives using the live disk also failed as the graphics card was not identified.
However the good news was that I could boot into Ubuntu and then the problem seemed clear.
This Dell PC (Dimension 2400) has a small FAT partition (about 49meg) which is /dev/hda1 - maybe this is where SGD was pointing?

So with a grub-install /dev/hda2 (using sudo of course) all was well.

I hope this is helpful

---

