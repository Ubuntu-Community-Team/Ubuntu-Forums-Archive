---
title: "Adding TV Out to a Twinview setup"
date: 2007-12-10
forum: General Help
---

### Post by bsander on 2007-12-10
Hi all,

I'm running a Twinview setup on my laptop with one additional screen. This all works fine. Now I'd like to add my TV-screen to this setup so that I can play videos on it. However, I don't want this "screen" to be part of my normal workspace, so that it becomes part of my normal desktop, for running programs and stuff (this is because the tv will be off most of the time, and three screens would be a little bit overkill ;)). I want it to be really separate and then use some command to start playing a movie on the TV.

So far, it kind of works. I've got this script:

```
#!/bin/zsh
xauth add :1 . e35a4dd7ad107110869f6972fa832666
xinit /usr/bin/xterm -ut -e \
  /usr/bin/mplayer -stop-xscreensaver -fs -vo sdl "$@" -- :1 -xf86config xorg-conf-tv

```

This starts a new Xserver with an xorg.conf that utilizes only the TV, and plays the video. However,  during that time my primary session (the laptop + second monitor) go dark, and I can switch between the TV and Twinview setups with Ctrl+Alt+F7 or F9, but I can't use them both at the same time :(

Who can help me improve this setup so that I can watch movies and browse the net at the same time? :)

---

### Post by leonidas666 on 2007-12-10
My Experience is that, while a graphics card may have 3 or more output connectors, most can at most only display two different pictures (unless it is a special card, which is advertised with this capabilities. Matrox makes this kind of cards.). So probably you could create a configuration where one of your desktops is mirrored in the tv, but you won't be able to create a independent picture on the tv (unless you switch off one of your desktops).
Is it possible to create such a configuration in windows? If not, chances are that your hardware does not support it.

---

