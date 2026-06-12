---
title: "How to get sound working with multiple cards?"
date: 2007-04-28
forum: General Help
---

### Post by phinn on 2007-04-28
So I never had a problem with sound in Edgy, but I recently installed Kubuntu 7.04. (Did a clean install first time in years)


Anyway, the ONLY place I can get my sound to work is with oldschool XMMS because I can manually selected my Audigy2 sound card.  Everything else in Kubuntu seems to wanna use my built in sound card and I can't find any way to set it!

This never happened before I K/Ubuntu and its quite strange.

Is this a bug? Or am I missing something.


Oh yea, something is wrong with that new (outdated) WINE package too, because it works for crap in Feisty.

---

### Post by phinn on 2007-04-28
Okay I found on another forum that apparently KDE doesn't seem to know how to let you change this yourself, which is no surprise because the KMix app is god awefull.


Anyway these two things will fix it for anyone else having this issue (from a google search there are quite a few)

do:
sudo asoundconf list
[example]
Names of available sound cards:
CK804
UART
Audigy2

pick the card you want and:

sudo asoundconf set-default-card Audigy2


It'll work. Hopefully it turns out there a GUI method so people don't have to go forum searching.

---

### Post by Ateo on 2007-04-29
thanks

---

### Post by Alfdog on 2007-05-21
this helped me with my audigy2 card and kubuntu 7.04, thanks alot

---

### Post by Co.Sinecure on 2007-06-17
Fantastic, thanks a lot. Fixed Ubuntu 7.04 for me.

---

