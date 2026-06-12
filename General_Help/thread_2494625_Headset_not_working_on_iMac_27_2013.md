---
title: "Headset not working on iMac 27 2013"
date: 2024-01-22
forum: General Help
---

### Post by jt4u on 2024-01-22
I recently installed 22.04 on an iMac 27 mid 2011 and was so impressed by it that I decided to give it to my son who had an aging laptop. Everything works fine on it AFAIK, including the headsets when plugged in.

Based on that positive experience, I decided to look for an iMac 27 for myself (my old 2009 DellDesktop is way past it's due date) and I got a slightly more recent one. It's a 2013 i7 that I upgraded to 32Gb of RAM while at it. It runs like a charm and will soon kick the old Dell away. 

But, I cannot get the wired headset through the jack in the back to work. It works fine when I boot MacOS, but is not recognized at all on ubuntu. I also managed to get bluetooth headsets to work, buty no luck with the plugged in headsets. 

I looked at alsamixer, added: 

[PHP]options snd-hda-intel model=imac27 position_fix=0[/PHP]

to the alsa-base-conf

But I still cannot get it to work. 

What am I missing here ?

---

### Post by jt4u on 2024-01-27
So I'm not sure what fixed it, but after installing Ubuntu Studio and adding options snd-hda-intel model=imac27_122 to the &#8203; alsa-base-conf it now works fine.[COLOR=#000000]

[/COLOR]

---

