---
title: "Sound in flash plugin for firefox skips after a few seconds"
date: 2006-11-12
forum: General Help
---

### Post by loftx on 2006-11-12
Hi There,

I'm experiencing a problem with the flash plugin for firefox. When I visit a site with flash which plays sound for an extended period of time e.g pandora.com after a little while (sometimes after just a few seconds or sometimes after a few minutes) the sound gets "stuck" and continues looping/skiping a small portions (like half a second or something) until I close the browser window containing the flash plugin. 

I'm running Edgy and installed the flash plugin using Automatix 2 if that's any help.

Thanks,

Tom

---

### Post by spidernik84 on 2006-11-12
Same problem here...flash 9 plugin, experiencing these problems in liferea too :(

---

### Post by greybirds on 2006-11-12
Ditto. Sites like youtube are useless now. I'm trying to isolate the problem and will post what I find.

---

### Post by stoffe on 2006-11-13
Not sure exactly what, but it's some kind of ALSA mixing or/and gstreamer issue, however turning off say Rhythmbox may not be enough as some other apps like OOo and Evince also seem to be able to hog the sound. It's a regression from at least Dapper, maybe more recently.

---

### Post by spidernik84 on 2006-11-14
try to install totem-gstreamer plugin, i'm testing it right now instead of the previously installed totem-xine. Dunno if this is the solution but everything is running smoothly ATM.

Command:

```
sudo aptitude install totem-gstreamer
```

---

### Post by stoffe on 2006-11-14
> **spidernik84 said:**
> try to install totem-gstreamer plugin, i'm testing it right now instead of the previously installed totem-xine. Dunno if this is the solution but everything is running smoothly ATM.

Command:

```
sudo aptitude install totem-gstreamer
```

Not sure what that would have to do with anything, especially flash, and totem-gstreamer is the default (and what I run) unless actively replacing it with the xine version.

---

### Post by loftx on 2006-11-14
I was running totem-xine before so tried installing totem-gstreamer - it makes no difference for me

---

### Post by Greg T. on 2006-11-16
Looping is a known problem in the Flash 9 beta (known to the developers, that is). They've indicated that fixing the audio problems is their [#1 priority]("http://blogs.adobe.com/penguin.swf/2006/11/chart_toppers.html").

---

### Post by spidernik84 on 2006-11-21
> **stoffe said:**
> Not sure what that would have to do with anything, especially flash, and totem-gstreamer is the default (and what I run) unless actively replacing it with the xine version.
Sorry, my mistake...i was dealing with totem problems too, so i mistaked :)

Anyway, GREAT news from adobe: Flash 9 Beta 2 is Out!!! Audio problems hopefully solved :D :D HORRAY!!!

[http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview)

---

### Post by stoffe on 2006-11-21
> **spidernik84 said:**
> Sorry, my mistake...i was dealing with totem problems too, so i mistaked :)

Anyway, GREAT news from adobe: Flash 9 Beta 2 is Out!!! Audio problems hopefully solved :D :D HORRAY!!!

[http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview)

Yup, and so far it seems to solve the problem for me at least with Flash + other apps, still some non-flash issues with ALSA mixing though.

---

### Post by voodoonirvana on 2006-11-25
> **spidernik84 said:**
> Sorry, my mistake...i was dealing with totem problems too, so i mistaked :)

Anyway, GREAT news from adobe: Flash 9 Beta 2 is Out!!! Audio problems hopefully solved :D :D HORRAY!!!

[http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview](http://labs.adobe.com/technologies/flashplayer9/releasenotes.html#overview)

Any idea when this comes out for Firefox 2?

---

### Post by stoffe on 2006-11-26
> **voodoonirvana said:**
> Any idea when this comes out for Firefox 2?

It works for Firefox 2 today, but you'll have to put it into the plugins directory manually while it is in beta. If you download it, it has a README that explains how you install and uninstall easily.

---

### Post by erissiva on 2007-03-06
I'm confused. I'm using Firefox 2.0.0.2 and Flash 9.0.31.0 (supposedly the newest) and I am still experiencing this issue. Is there a way that I can resolve it?

---

