---
title: "Last (default) option text in GRUB not dispalyed"
date: 2007-08-16
forum: General Help
---

### Post by jano_rajmond on 2007-08-16
Ok, so I modified my GRUB menu.lst file.

I previously had Windows XP installed and now switched to Windows 2003 server and modified the text entry in the menu.lst file from Microsoft Windows XP to Microsoft Windows 2003 Server.

Also I removed the last 3 options from GRUB which were incorrectly identified as bootable Windows XP partitions. 

I also played around with the colors, but then commented the color option, so now the menu is black and white.

The GRUB menu now when it appears the last entry (which is also the default Windows 2003 Server entry) text is not displayed, only the cursor is visible. When I move the cursor the text appears and everything works normally from then on. Also GRUB works just fine... even if the text is not visible.

My hunch is that the cursor is painted over the text... and that is why is not visible.

Anyway, is there a way to work around this problem so the default entry would be visible?

It just really bugs me and also others who use my computer (like my psycho roommate) might get really stressed if he doesn't sees what he's booting into.

PLS HELP!

Thanks!

---

### Post by matthew.lns1 on 2007-08-16
I would try recomenting ( placing a # before ) the line were you set the colors. I noticed it is commented by defalt.

---

### Post by jano_rajmond on 2007-08-16
Already did that... but still does the same thing even in B/W.

---

### Post by loserboy on 2007-08-16
you could reinstall Grub

---

### Post by matthew.lns1 on 2007-08-17
How are you supposed to enter the colors?

---

