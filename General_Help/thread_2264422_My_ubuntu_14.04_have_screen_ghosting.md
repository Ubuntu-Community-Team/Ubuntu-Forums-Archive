---
title: "My ubuntu 14.04 have screen ghosting"
date: 2015-02-07
forum: General Help
---

### Post by kamimoto0127 on 2015-02-07
[https://www.youtube.com/watch?v=WqhkpU2K0dE](https://www.youtube.com/watch?v=WqhkpU2K0dE)

[COLOR=#333333][FONT=arial]Hi I tried xubuntu lubuntu ubuntuMATE 14.04[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]but all distros made screen ghosting[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]any clue?[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]My system uses intel pentium j2900 with 4GB RAM and uses intel graphics[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]it uses i915 driver

And even my i7 3770 with intel graphics have same issue

Seems like intel HD graphics have problem...[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-02-07
> [COLOR=#333333][FONT=arial]Seems like intel HD graphics have problem...[/FONT][/COLOR]That's an interesting comment as Intel graphics usually work with no problems; they certainly do on my machine with an Intel i5-3570K cpu using HD4600 graphics.

What other hardware have you got?

Can you show a screenshot of exactly what you mean by "ghosting" please, if you can get one; usually Print-Screen key will offer to save one in Xubuntu, and do it automatically in Lubuntu by putting a **scrot** image in your home.

---

### Post by kerry_s on 2015-02-07
it's your screen, ghousting would stay there. i'm going to guess your monitor/tv has probably high refresh rate(whatever its called), 16ms or more.

---

### Post by kamimoto0127 on 2015-02-07
well I uploaded youtube video

I think "screen ghosting" is not right word

Its more like frameskip

ADD : I just tried lubuntu 12.04 and ubuntu 12.04.5

Ubuntu 12.04.5 made perfect displaying without frameskip

Maybe i should find difference from ubuntu 12.04.5

---

### Post by mc4man on 2015-02-07
What you're seeing, showing in vid  is horizontal tearing (no vsync
Don't use xubuntu so don't know how to fix.

---

### Post by kamimoto0127 on 2015-02-07
Oh i just install ubuntu 14.04.1 and have perfect displaying

seems like unity have good compatibility with me.... LOL

But Unity is uncomfortable....

---

### Post by kamimoto0127 on 2015-02-07
Okay I just got a solution

Installed compton and run this
compton --vsync opengl

now tearing just gone

Thanks guys!

---

