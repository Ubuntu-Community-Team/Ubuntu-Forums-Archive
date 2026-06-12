---
title: "keeping installed programs and stuff to easily transfer to another disk"
date: 2007-07-01
forum: General Help
---

### Post by marshall.robert on 2007-07-01
hi, i have unexpectedly used ubuntu more than i foresaw and i would like to increase the partition i have for it, but i dont want to have to install all my programs and set up everything again. could someone kindly let me know if there is any possible way of achieving this and if so how to do so?

thanks
-rob

---

### Post by earobinson on 2007-07-01
u should be able to use the live cd to do this

---

### Post by marshall.robert on 2007-07-01
how do you mean?

---

### Post by milton1 on 2007-07-01
You may also want to investigate the GParted Live CD. It seems to have fewer problems resizing and moving partitions than the Ubuntu Live CD has; mostly because it will not automount your partitions on boot.

---

### Post by earobinson on 2007-07-01
> **marshall.robert said:**
> how do you mean?
you should be able to use the live cd (or gparted live cd) and run gparted to resize your partition

---

### Post by marshall.robert on 2007-07-01
> **earobinson said:**
> you should be able to use the live cd (or gparted live cd) and run gparted to resize your partition

i had thought about that but im rather paranoid about loosing everything...

---

### Post by marshall.robert on 2007-07-01
ok, here is what i was thinking of:

the attached image is a gparted view of my harddrive.

i would like to get rid of the extended partition altogether (including everything in it), but thats where my root lies. i would like my root to be hda2 by the end of it, this would give me about 100gb for ubuntu instead of the 20 it has now. (maybe i could acomplish this by formatting hda2 and copying the entire contents of my root drive to it, then editing grub to adapt to it).

if i cant do that then i would like to make the whole of the extended partition dedicated to ubuntu (except for the swap). this would probably be the easiest to achieve but i have never resised a partition before, so i am not really sure about it. this would give me about 80gb.

thanks for the quick responses so far
-rob

---

### Post by milton1 on 2007-07-04
You can use GParted to copy your root directory to hda2 (assuming it is blank), then test to see if it boots (you will need to edit /boot/grub/menu.list to make it point to the correct partition), and if it works, start moving things around and resizing/deleting whatever partitions you want. Of course, as always, BACK UP YOUR DATA FIRST! GParted works well, but there is always the possibility of disaster, no matter how good your software is.

---

