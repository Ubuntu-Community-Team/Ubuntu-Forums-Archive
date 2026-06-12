---
title: "Wired"
date: 2005-04-28
forum: General Help
---

### Post by Bloke on 2005-04-28
Anyone try this with Ubuntu?

[http://bloodshed.net/wired/](http://bloodshed.net/wired/)

---

### Post by kiddo on 2005-04-28
I haven't been able to make it work. Ever. I hope I will someday, because audacity is pretty limited (and ugly!) for me. It would be nice to have it in the repos.

---

### Post by XDevHald on 2005-04-28
Would be more useful to the people who do music recording and etc, but no, I've never tried it. Looks interesting.

---

### Post by philipacamaniac on 2005-04-28
I'm VERY interested in getting Linux to work as my full-time audio production desktop. The main problem is latency and professional hardware compatibility. I've always used ardour, but this looks GREAT, especially since it is a KDE app, and I'm a KDE addict.

I'll try when I get the chance. It looks very promising. I vote to put it into universe.

---

### Post by EricS on 2005-05-08
[QUOTE=philipacamaniac]I'm VERY interested in getting Linux to work as my full-time audio production desktop. The main problem is latency and professional hardware compatibility. I've always used ardour, but this looks GREAT, especially since it is a KDE app, and I'm a KDE addict.

I'll try when I get the chance. It looks very promising. I vote to put it into universe.[/QUOTE]
No, it's a GTK app.

I've gotten Wired to work by adding a 3rd-part repository. I'll quote a post from the Wired-forums:
> hi, 
just sorted out an apt source for wired with josh from dotmepis.org 
deb [http://apt.dotmepis.org/mepis](http://apt.dotmepis.org/mepis) stable main contrib non-free 
deb [http://apt.dotmepis.org/mepis](http://apt.dotmepis.org/mepis) testing main contrib non-free 
either apt-get install wired or 
apt-get install wired-cvs 
wxWidgets issue is taken care of. 
save settings crash is also fixed. 
post any installation woes @ dotmepis.org's bugzilla. 
freecycle is also in the repository.... 
[http://www.redsteamrecords.com/freecycle/](http://www.redsteamrecords.com/freecycle/) 
cheers, 
mat


Put it into /etc/apt/sources.list and TADA! :)

---

### Post by philipacamaniac on 2005-05-09
[QUOTE=EricS]No, it's a GTK app.[/QUOTE]

Whoops! Yeah, I guess it uses wxWidgets. The screenshots all show KDE Window Decorations, so I was "misinformed", but I guess the generic X windows icon should have clued me in. I still want to try it. Are there any major differences/advantages between Wired and Ardour?

---

### Post by EricS on 2005-05-14
Ardour is more mature, but doesn't have midi-support.
Wired aims higher with "rack"-based synths/drum-machine etc built in, but doesn't run stable at all om my machine. (couldn't get audio-recording working at all)

Also, Ardour uses Jack which is very handy if you want to sync/connect it with other applications like hydrogen (a drummachine).

Yep, that's pretty it. I'm gonna stick with ardour until Wired becomes more stable or Ardour gets midi-support (which is the plan).

If you're fond of kde, there's always Rosegarden. Which is supposed to be very competent.

---

### Post by maltje on 2005-05-16
[QUOTE=EricS]No, it's a GTK app.

I've gotten Wired to work by adding a 3rd-part repository. I'll quote a post from the Wired-forums:


Put it into /etc/apt/sources.list and TADA! :)[/QUOTE]

Is the ftp site ok???
Won't work for me!!!!

---

### Post by EricS on 2005-05-17
[QUOTE=maltje]Is the ftp site ok???
Won't work for me!!!![/QUOTE]

Nope, me neither. Dunno why it stopped working.

---

### Post by Bloke on 2005-07-01
Bump*

---

