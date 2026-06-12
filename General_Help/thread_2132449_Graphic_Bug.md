---
title: "Graphic Bug"
date: 2013-04-04
forum: General Help
---

### Post by steffen90 on 2013-04-04
Hey guys, 

I'm experiencing this bug on my screen, not sure what might be causing it... Anyone?

[ATTACH=CONFIG]240960[/ATTACH]

---

### Post by Impavidus on 2013-04-05
Graphics driver problem?

If proprietary drivers are available for your video card, have you tried installing them? Or is this a very recent card? In that case open source drivers may not be completely debugged, leaving artefacts like that. Could you post the make and model of your video card?

---

### Post by slickymaster on 2013-04-05
> **Impavidus said:**
> Graphics driver problem?

If proprietary drivers are available for your video card, have you tried installing them? Or is this a very recent card? In that case open source drivers may not be completely debugged, leaving artefacts like that. Could you post the make and model of your video card?

Hi, welcome to the forum.

If you don't know how to get what Impavidus requested, just open a terminal and run the following command:
```
lspci | grep VGA
```
More detailed information can be found by running:
```
sudo lshw -C video
```

---

### Post by steffen90 on 2013-04-07
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

So... what does it mean ? hehe

Thanks for the help guys

---

