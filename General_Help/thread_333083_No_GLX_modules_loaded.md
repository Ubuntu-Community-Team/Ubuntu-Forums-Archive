---
title: "No GLX modules loaded"
date: 2007-01-06
forum: General Help
---

### Post by stizuart on 2007-01-06
I made a big mistake. I had tried to install compiz and/or beryl. I could not get either to run and glxgears went from ~4000fps to ~800fps. The last straw was that video was choppy. So I thought that re-installing the nvidia drivers would solve the problem(thinking about it now, I don't know why I thought this). I had the envy script, so I thought that I would use that, in gnome. it kicked me back to terminal and since then I have not been able to get back into gnome.

I have tried possibly everything that I could find on the forums that could help to ne avail. So I hope that this hasn't been posted and solved yet. This is what I get when I try to start X,

dlopen; /usr/lib/xorg/modules/xgl/libglx.so cannot open shared object
file: no such file or directory

Fatal server error:
No GLX modules loaded

dlopen: /usr/lib/xorg/modules/xgl/libglx.so cannot open shared object
file: no such file or directory

FatalError re-entered, aborting
No GLX modules loaded

I may have screwed up the code, hopefully it is clear enough. I have tried it with GLX removed, GLX installed, default xorg.conf, custom xorg.conf, autodetect xorg.conf, etc,etc, ad nauseam. I hope that someone can shed some light on this, because I am certainly in the dark.

In case it helps I am running a celeron 3.something, 1gig of ram, and a nvidia 6600. All of this was running perfectly before my botched compiz/beryl installs.

---

### Post by tseliot on 2007-01-07
1) Download the latest Envy:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
```

2) Install Envy:
```
sudo dpkg -i envy_0.7.5*.deb
```

2) make sure you are in the command line (you don't have to run it in a desktop environment such as GNOME) and type:
```
envy
```

P.S. make sure that all your repositories are enabled

---

