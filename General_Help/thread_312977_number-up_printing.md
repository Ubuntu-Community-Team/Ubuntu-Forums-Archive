---
title: "number-up printing"
date: 2006-12-05
forum: General Help
---

### Post by sha_man on 2006-12-05
hello,

i installed my HP Laserjet 1018 (local) and the printer works. But not too well in fact :( : I want to print multiple pages on 1 page (n-up), but if I select this in the printer dialog, it does not follow the instructions and simply prints the pages normally.
However, doing for ex. ```
lpr -o number-up=2 filename.pdf
``` **is working**. But it's not a very elegant way to print like that... especially when the printer dialog should allow these options. 
What could I do?

---

### Post by engla on 2006-12-05
Hey, I have the same problem. I researched this on launchpad (the ubuntu bug database), and I found two things:

[this bug in the old print system  (gedit)]("https://bugs.launchpad.net/distros/ubuntu/+source/libgnomeprint/+bug/3667") -- not fixed at all
[This bug in the new print system! (evince etc)]("https://bugs.launchpad.net/distros/ubuntu/+source/evince/+bug/67164") -- fixed in upstream

It's ironic to note that the same bug is in two separate (equal to the user) libraries for printing in gnome.
It seems like this issue is fixed in evince in upstream, but there is no update for edgy so far. Perhaps we can get the backports team to help out with this (as soon as the fix is in feisty) ?

---

### Post by sha_man on 2006-12-06
i would really appreciate that :) 
this a critical bug (an important feature is not available)

---

### Post by alexanderfrey on 2007-05-01
Hi There,

I tried to print with my HP 1018 Laserjet but it doesn't work. The printer is automatically detected when I install a new printer but after the installation it doesn't print. I can send printing jobs to it from Firefox or Openoffice but the printer doesn't do anything.


Can please someone help me ?

I use ubuntu feisty.


Thank you ,Alexander

---

### Post by alexanderfrey on 2007-05-01
By the way, the 1018 is connected via USB.

---

