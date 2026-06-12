---
title: "Installing XP on Ubuntu Box"
date: 2007-08-07
forum: General Help
---

### Post by WastingBody on 2007-08-07
I want to install Windows XP on my Ubuntu box. I'm not completely sure how it will work so thats why I'm asking. I have another blank HDD that I could use for the XP installation if that would be best.

---

### Post by Harika on 2007-08-08
From my (very) limited knowledge, you would have to load XP first, then load Ub on top, XP will try to erase Ub if you go in the other order.

If you install XP on a dif drive, you will probably have to edit the grub loader. (I have no Idea how to do this) Otherwise you could not get into both OS's.

Untill a more knowledgeable person posts I hope this is a step in the right direction.

---

### Post by scrooge_74 on 2007-08-08
It is not so much that XP will erase Ubuntu, it will erase grub from the MBR and then you will need to reinstall GRUB.
I think you have to let XP boot from the first drive (you need to rearrange the order of the drives) and tell GRUB the new order later on

---

### Post by UK-Wobbie on 2007-08-08
> **WastingBody said:**
> I want to install Windows XP on my Ubuntu box. I'm not completely sure how it will work so thats why I'm asking. I have another blank HDD that I could use for the XP installation if that would be best.

Get your self VirtualBox! I had WinXP working on my Ubuntu 7.40 and it works OK :)
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) I hope that will help you out :)

---

