---
title: "APTonCD"
date: 2007-07-14
forum: General Help
---

### Post by guitarmaniac on 2007-07-14
Is there a way of changing what temp directory APTonCD uses?
My root partition (which included my /tmp folder) is nearly full so I when I try to create an APTonCD ISO it just freezes cause there isnt enough room on my /tmp folder for the archive.

---

### Post by Happy_Man on 2007-07-14
Can't you just delete the stuff in your /tmp folder? It's not very important, anyway.... ;)

---

### Post by guitarmaniac on 2007-07-14
Theres not enough space on the root partition left even if I delete the contents of /tmp.

---

### Post by kelvin spratt on 2007-07-14
looking at my version of apt i can save to any file or partition on my computer press restore and it then asks you where you want to save your file,

---

### Post by guitarmaniac on 2007-07-14
Thats correct it will save the ISO to any directory you want, but it needs to use the /tmp folder in the background.

I think I may have a solution.
If I move all the deb packages in /var/cache/apt/archives to my home partition that should free up enough space and I'll just point APTonCD to the debs manually.

---

