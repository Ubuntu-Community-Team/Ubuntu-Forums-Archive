---
title: "Mplayer totem-xine"
date: 2004-12-10
forum: General Help
---

### Post by bruno on 2004-12-10
Hello
I need play divx dvd etc...


When i installed Ubuntu for thr first time few day after RC release 
no problem 
apt-get install mplayer from marillat
But now for a new install : 
 mplayer-586: Dépend: libarts (>= 4:2.2.2-1) mais il n'est pas installable ou
                       libarts-alsa (>= 4:2.2.2-1) mais il n'est pas installable               Dépend: libdirectfb8 mais il n'est pas installable
               Dépend: libdvdread2 mais il n'est pas installable
               Dépend: libvorbis0 (>= 1.0rc3-1) mais il n'est pas installable
 :sad: 
who can and how solve this problem??

if I want install totem-xine

Les paquets suivants seront ENLEVÉS (REMOVE):
  totem-gstreamer ubuntu-desktop
Les NOUVEAUX paquets suivants seront installés :
  totem-xine

It seems not a good idea.....? what you mean??

I follow also 
[http://ubuntuguide.org/](http://ubuntuguide.org/)
to install
gstreamer0.8-plugins
but IS totem-gstreamer able to play something?????

tks for your answerS
Bruno

---

### Post by Hikaru79 on 2004-12-10
I would give up on Mplayer and totem-xine and try gxine. It's the one I've had the fewest problems with, and it's got all the same features (more, really, like improved streaming support).

Simply ```
sudo apt-get install gxine
```

---

### Post by bruno on 2004-12-11
tks for the answer but
there is a lot of player like vlc who can play simple

But mplayer is need for vesa driver output support that able me to use tv-out (ATI...)

and as I remember it use less CPU.. for the moment I can't play DVD on my box 
(P2 450 xeon)

Is marillat problem package???
or Ubuntu-desktop?gstream?

tks

---

