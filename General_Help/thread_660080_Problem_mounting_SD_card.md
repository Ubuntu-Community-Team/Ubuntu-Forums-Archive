---
title: "Problem mounting SD card"
date: 2008-01-06
forum: General Help
---

### Post by IvoLimmen on 2008-01-06
Hi,

I hope I am posting this in the right forum. I have an SD card that I access using my HP PSC 2175. This has been going well for a long time now. I am using Ubuntu gutsy since a while and for the first time I am having problems.
Suddenly my card was mounted read only and I could not use SUDO (under a terminal) to remove my pictures. A few minutes ago when I moved pictures from my card it wend ok... so why it suddenly stopped working I have no clue.
I found out that I could set mounting options using nautilus when I access my SD from my desktop. Being an experienced user I though I could give it a try. I added new mounting options and leaving the 'ro' option out (that of course stands for readonly).
Next I unmounted my card and reinserted it into the card reader. It gave me a strange error that the path was incorrect. Now I cannot access my card anymore.
I tried fixed the problem but I can not find the options I entered. I tried looking within my UDEV rules under /etc/udev/rules.d but I can not find it. Then I started search for HAL hoping it would be located here but I can not find where nautilus changes the settings for my SD card so I can change it back..
I also looking in the fstab and mtab but these do not contain these settings...

I hope someone knows how to undo my fault because I would find it very stupid to reinstall my system because I change a setting...

---

