---
title: "Problem with colour using w32codecs"
date: 2006-11-06
forum: General Help
---

### Post by pstewart on 2006-11-06
I've recently done a clean installation of Edgy and installed the w32codecs package using Automatix (and again manually, just to be sure that Automatix wasn't the problem). I can play video files in Totem, but the colour seems very bright and "washed out".

Totem + w32codecs worked flawlessly in Dapper with the same files. I used easyubuntu for that though IIRC.

I posted [this]("http://www.ubuntuforums.org/showthread.php?t=292953") a couple of days ago in the Multimedia forum. Someone suggested it may be due to using very low bit depth with very high brightness and/or contrast, but was also in need of a solution.

Has anyone else had this problem? Any ideas on how to fix it?

Cheers,
Peter

---

### Post by zgornel on 2006-11-06
Adjust constrast settings. I use mplayer so I edited ~/.mplayer/config and added this line *contrast = -45*. Adjusting contrast goes for all players.

---

### Post by pstewart on 2006-11-06
Thank you. I use Totem, so I changed the sliders in the preferences menu. I'm actually a little embarrassed that I didn't think of that myself!

Thanks again!

---

### Post by zgornel on 2006-11-07
> **pstewart said:**
> Thank you. I use Totem, so I changed the sliders in the preferences menu. I'm actually a little embarrassed that I didn't think of that myself!

Thanks again!
It took me a week :D

---

