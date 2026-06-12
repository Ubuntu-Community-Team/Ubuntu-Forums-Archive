---
title: "Kfloppy wont format my floppy, any ideas ?"
date: 2005-03-20
forum: General Help
---

### Post by TasKiNG on 2005-03-20
I am trying to format a floppy disk using Kfloppy.

I have tried running it with and without the floppy mounted but get the same error

'Cannot access /dev/fd0u1440 Make sure that the device exists and that you have write permition to it'

I have tried running kfloppy as user and root but get same error

I can read and write to he floppy ok though.

There is no /dev/fd0u1440 however there is a /dev/fd0

thought I may have to configure kfloppy to use /dev/fd0 but cant find any settings to change.

Any help would be appreciated

Cheers

---

### Post by TasKiNG on 2005-03-20
Ok managed to fix this myself. Just created a link to /dev/fd0 called /dev/fd0u1440

---

### Post by cintra on 2005-05-06
[QUOTE=TasKiNG]Ok managed to fix this myself. Just created a link to /dev/fd0 called /dev/fd0u1440[/QUOTE]
Would just like to thank you from Gentoo for this simple workaround :-D

This is a  problem with udev not producing the floppy devices kfloppy expects. A KDE bug has been logged, but no suggested fix yet..

regards

---

