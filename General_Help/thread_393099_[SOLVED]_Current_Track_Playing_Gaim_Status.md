---
title: "[SOLVED] Current Track Playing Gaim Status"
date: 2007-03-25
forum: General Help
---

### Post by reclusivemonkey on 2007-03-25
I know a lot of people have been asking about this, so I was quite pleased to find this today;

[http://jon.oberheide.org/projects/gaim-rhythmbox/](http://jon.oberheide.org/projects/gaim-rhythmbox/)

Allegedly it uses the current playing track in Rhythmbox as a status message in Gaim (yes, yes I know this is an abuse of the status message, but this is exactly the sort of thing people coming from Windows want to see in their desktop setup).

However, as always, trying to get things to compile in Ubuntu is a PITA. I get the following error;

```

checking for gaim... configure: error: Package requirements (gaim >= 2.0.0) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables gaim_CFLAGS
and gaim_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've tried adding to the PKG_CONFIG_PATH and using the gaim_CFLAGS to no effect. Can anyone without a screaming seven month old in the background tell me how to compile this plugin? TIA.

This would be a great addition to Rhythmbox, as its the default music player in Ubuntu and Gaim is the default messenger.

---

### Post by kwaanens on 2007-03-25
> **reclusivemonkey said:**
> This would be a great addition to Rhythmbox, as its the default music player in Ubuntu and Gaim is the default messenger.

I've been looking into this too. There's also a gaim-plugin for amarok which is a KDE-player that also a lot of Gnome users use. (However it eats cpu in Gnome, due to a bug. (A constant 50% of one of my processors))

I'd rather like to see a Gaim-Last.fm-NowPlaying-plugin. That would work with amarok, rhythmbox, banshee, xmms, bmp, etc.

- Ketil

---

### Post by reclusivemonkey on 2007-03-25
Well I got a little further. I installed gaim-dev which fixed the gaim problem. I now get 

```

checking for gtk2... configure: error: Package requirements (gtk+-2.0 >= 2.4) were not met:

No package 'gtk+-2.0' found

```

I've looked for some gtk-dev packages but don't seem to be able to find any.

---

### Post by haricharan on 2007-03-25
try installing libgtk2.0-dev and all its dependencies...

---

### Post by reclusivemonkey on 2007-03-25
> **haricharan said:**
> try installing libgtk2.0-dev and all its dependencies...

D'OH! of course =] Thanks for that. That also helped me with the next few errors. Its compiling now...

---

### Post by reclusivemonkey on 2007-03-25
Sweet, its all working now. Just in case anyone else fancies trying this, here's what you need to do;

Grab the lastest version of the plugin from [http://jon.oberheide.org/projects/gaim-rhythmbox/](http://jon.oberheide.org/projects/gaim-rhythmbox/)

Install "build-essential"

Install the following;

[LIST]
[*]gaim-dev
[*]libgtk2.0-dev (lots of dependencies here)
[*]libdbus-1-dev
[*]libdbus-glib-1-dev
[/LIST]

then just ./configure, make, sudo make install

The configuration is done in Gaim rather than Rhythmbox.

---

### Post by haricharan on 2007-03-26
cool :D

---

### Post by mpp on 2007-06-18
It doesn't compile for me (feisty) ... it still complains about missing pidgin.

How do I set the ```
gaim_LIBS
``` and ```
gaim_CFLAGS
``` to get around this?  I don't understand this bit.

have fun()
mike

EDIT: I've used the gaim beta package from the website and it worked fine, ie this one: [http://jon.oberheide.org/projects/pidgin-rhythmbox/downloads/gaim-rhythmbox-2.0beta5.tar.gz](http://jon.oberheide.org/projects/pidgin-rhythmbox/downloads/gaim-rhythmbox-2.0beta5.tar.gz)

---

