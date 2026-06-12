---
title: "deltree equivalent"
date: 2007-04-17
forum: General Help
---

### Post by dgrafix on 2007-04-17
how do i delete directories, using rmdir can only be done if dir empty

the other thing is nautilus scripts, where are they stored, I had some good ones put there by automatix to get a root nautilus window. This is gone now ive installed fiesty (but still have all my dapper files :) I just need to know where they are.

Edit-- 

I know about  "sudo rm -r  dirname "  but this is REALLY slow, is there a faster way?

---

### Post by Subban on 2007-04-17
delete directories with
rm -r /foldername/

Being very careful with it ;)

Naultilus scripts live in:
~/gnome2/nautilus-scripts/

---

### Post by earobinson on 2007-04-17
also if its a big folder you can use rm -rf so that it wont check before removing the file. ```
man rm
``` for more info

---

### Post by dgrafix on 2007-04-17
lol thanks.

Its really slow though,

i wanted to delete everyrhing on my sync drive (my 2nd hard disk mirrors my first) with:
/media/drive# sudo rm -r  *

It worked, except it took like 15 minutes!

Now t try and get the root-nautilus-here script working again.

:guitar:

---

### Post by earobinson on 2007-04-18
Glad to know it works, it takes time to remove all those files.

---

