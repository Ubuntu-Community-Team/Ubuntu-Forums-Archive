---
title: "Sound problems"
date: 2008-07-02
forum: General Help
---

### Post by ioniviil on 2008-07-02
I don't know if this is the exact forum to place my question, but on Media and Sound it looks like everyone else was on a different "vibration". And besides my problem is not exactly a problem.. well, here it goes:
I am using ALSA to to handle sound on my system, it works perfectly except for one thing, only one application at a time is able to use it :( , I read somewhere that starting from Hardy Heron that would not be a problem, but I am still experimenting it. Maybe I am just wrong and still ALSA responds to one a application at a time.

Any help to dissipate my ignorance is appreciated :)

---

### Post by jocko on 2008-07-02
What you need is a software mixer to mix the sounds before they are sent to the soundcard.
Before hardy, the default software mixer was esound (plus the possibility to activate an alsa software mixer plugin, dmix), but starting with hardy the default is pulseaudio (which is why hardy was suppsed to solve this problem, as you are no longer forced to figure out how to configure alsa to do software mixing).

So either make pulseaudio the default sound output in all your apps (it will still use alsa, it's just that pulseaudio takes care of the mixing before the signal is passed on to alsa).

Or set up alsa to use the dmix plugin instead of direct hardware access by default.
One way to do this:
1. First find how your soundcard is named by asoundconf:
```
asoundconf list
```2. Have asoundconf set that card as default and generate a default configuration file (which makes dmix the preferred device):
```
asoundconf set-default-card [COLOR=DimGray]*name*[/COLOR]
``` (where [COLOR=DimGray]*name*[/COLOR] is the output from the previous command).

I'm not sure which is best, but if you use alsa/dmix, pulseaudio will not be very happy, which means no system sounds will work...

---

### Post by soccerboy on 2008-07-02
you can enable pulseaudio by installing pulseaudio-manager and working from its gui.

---

### Post by jocko on 2008-07-02
Edit: Double post when i tried to edit my previous post...

---

### Post by ioniviil on 2008-07-03
Thank you guys, you resolved my problem :)

---

