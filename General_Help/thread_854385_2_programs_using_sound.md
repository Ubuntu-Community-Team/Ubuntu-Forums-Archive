---
title: "2 programs using sound?"
date: 2008-07-09
forum: General Help
---

### Post by underworld288 on 2008-07-09
I don't know if this is really a problem, it's more of an inconvenience,  but when I have two apps open that use sound only one of them actually produces sound.

ex. I have Firefox open listening to my myspace profile song and Rhythmbox open listening to music. Only one app will have sound coming out of my speakers, it's always the app that was open first.

---

### Post by jocko on 2008-07-09
The simplest way to fix it is by setting all applications to use pulseaudio, which will act as a software mixer.
To get flash in firefox to use pulseaudio instead of alsa, you need to install the package libflashsupport, which is in the hardy repos.

Another way is to set alsa to use a pulseaudio plugin as default, as described [on this page]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") (step 1 and 2, step 3 is probably not necessary for what you want).
This means even applications that are set to use alsa, or which lacks their own pulseaudio output plugin will be mixed by pulseaudio before they are sent to the sound card.

---

### Post by underworld288 on 2008-07-09
will this mess with wine? I've heard that wine isn't compatible with pulseaudio.

---

### Post by jocko on 2008-07-09
> **underworld288 said:**
> will this mess with wine? I've heard that wine isn't compatible with pulseaudio.

I'm not sure about that, I don't use wine.
I would guess that if you use my second suggestion (the alsa pulseaudio plugin) and set wine to use alsa it would work, as wine would use it's alsa output plugin...

EDIT: I tested sound in winecfg with alsa as output, with alsa using the pulseaudio plugin as default, and it worked fine.

---

### Post by isaacj87 on 2008-07-09
Have a look at this incredibly useful thread...It gave me back the ability to have multiple programs use the sound server.

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by underworld288 on 2008-07-09
I used your link isaacj87 and now when i go to a flash site like myspace it says I don't have flash installed but I do have it installed.

---

### Post by isaacj87 on 2008-07-09
> **underworld288 said:**
> I used your link isaacj87 and now when i go to a flash site like myspace it says I don't have flash installed but I do have it installed.

The best idea is to remove the Flash that you installed (whichever way you installed it, via synaptic or the tar.gz), and follow the guide I posted carefully. I can't remember which part it is, but there's a section in the link that takes you through the process of installing Flash *and* how to get it properly configured so that it doesn't hog the sound server. Maybe there are two instances of Flash installed and that could cause conflicts.

You can see if Flash is truly installed or not (and possibly to see if there are two versions installed as well).

Inside Firefox, go up to the address bar (where URLs are typed) and type:

```
about:plugins
```

From there, see if Flash truly is installed.

---

