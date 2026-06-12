---
title: "does not reboot after update"
date: 2006-11-06
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-06
after **"BOINKING"** my machine really good, I re-installed with a dapper disc and then upgraded to Edgy. When I re-booted start-up presented me with a black screen with blinking curser in top left corner. I shut it down the hard way and re-booted to recovery mode and that is where I am at this point, A screen with a bunch of writng and  on the bottom is my name and curser.Lucky that I have another machine that I haven't **"Tweaked"** (broke)! Of course it's my fault for **"Tweaking"** and not leaving well enough alone that caused me to re-install. Dah !:(  **SOLVED******

---

### Post by _lynX on 2006-11-06
Are you using an nVidia or ATI video card? I've heard that after updating, a video driver reinstall is mandatory for these two.

Hope this helps!

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
I wish, as I have old Intel  graphics card and it's not supported any more. I figured out after searching in the forum. Solution was: sudo reinstall install --xserver-xorg or some thing like that as I do not remember from 2 hours ago. But after typing that in (recovery mode) screen flashed abit and holy s*it, desktop popped open.  (taurus where were u when I needed u?) **[B]SOLVED**[/B]

---

### Post by Hemmer on 2006-11-06
im not sure if this is any help, but after **each** i update i have to manually edit Xorg.conf to suit my graphics card in safe mode - i.e. change it back from "nv" to "nvidia". :/

---

