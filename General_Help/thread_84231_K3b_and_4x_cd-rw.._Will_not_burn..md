---
title: "K3b and 4x cd-rw.. Will not burn."
date: 2005-10-30
forum: General Help
---

### Post by floyd27 on 2005-10-30
Hi..
I have cd-rw's that are only 4x..
They work in windows dso i know its not a cd problem..
K3b says cant burn a low speed disk with a high speed burner..?
Does anyone know how to fix this problem?

---

### Post by shinygerbil on 2005-10-30
Have you made sure you're only trying to burn the cd at 4x?

Unless it's something odd with the hardware... My 24x burner won't burn at anything higher than about 4x, no matter what I do, but it works fine in Windoz..

Steve

---

### Post by floyd27 on 2005-10-31
Hi..
Yes i have tries 2x and 4x..When i put the cd in these are the only options that appear...Then i get the error message when it tries to start....

As for yopur problem.. try turning dma on (its in the guide).. and then do this..

sudo hdparm -E24 /dev/cdrom     (24 is max speed and you may need to change cdrom to your setup..mines /dev/hda....) it goes by IDE location.

---

### Post by Teroedni on 2005-10-31
Maybe you can try gnomebaker?

---

### Post by floyd27 on 2005-10-31
yea i tried that and another one as well..
no linux prog seems to want to burn it..?
I will try nero linux even though im not a fan of it...But i dont know why the other apps dont work...
it seems others are able to burn 4x cd's..?
........................................................................................................
There are only a few things that keeps me having a windows partition.. and all of them are related to my dvd burner in some way or another....

-Cant mount bin/cue files
-cant slow the drive down ..always at 56x ..
-cant burn 4x cdrw
-*slow ripping (fixed this yesterday)

---

### Post by earobinson on 2005-10-31
lots of people are having this problem

---

