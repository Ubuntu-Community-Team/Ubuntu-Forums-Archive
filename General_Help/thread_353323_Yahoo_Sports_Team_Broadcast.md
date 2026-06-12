---
title: "Yahoo Sports Team Broadcast"
date: 2007-02-04
forum: General Help
---

### Post by vol_freak on 2007-02-04
I subscribe to this service so that I can listen to my teams audio broadcasts over the internet. However, the files don't seem to want to play under firefox in Ubuntu 6.10. 

I get the following error

```
Totem could not play 'mms://dalwmle009.bcst.yahoo.com/__S__y949017_104741?StreamID=33412747=00448ED8EC4758CD4411D3D9EB45C62870=1552015=182747=2022057433=y=9006id12sbas445c6286e=04f7cc2f66fafd6545c7448a28b29ba3=UQ5kWpShdZOsQM9wcIBOrg--=1170614382'.

There is no input plugin to handle the location of this move
```

It appears to be a streaming wma. I am able to play wma files on my desktop with totem movie player.

---

### Post by mgmiller on 2007-02-04
Try installing media player connectivity.  It will allow you to specify what player to use for what streaming formats in Firefox.  Get it here:

[https://addons.mozilla.org/firefox/446/]("https://addons.mozilla.org/firefox/446/")

After it's installed, you will have to restart Firefox.  Look in the Tools menu for media player connectivity and click on the configure option.  I have windows media set to use /usr/bin/vlc.  I find that works pretty well most of the time.  If you have no problems playing wma's in totem, you could also try /usr/bin/totem as the command.  The nice thing is you don't have to restart Firefox each time.  Just try the different player and re click.

Good Luck.

---

### Post by vol_freak on 2007-02-04
> **mgmiller said:**
> Try installing media player connectivity.  It will allow you to specify what player to use for what streaming formats in Firefox.  Get it here:

[https://addons.mozilla.org/firefox/446/]("https://addons.mozilla.org/firefox/446/")

After it's installed, you will have to restart Firefox.  Look in the Tools menu for media player connectivity and click on the configure option.  I have windows media set to use /usr/bin/vlc.  I find that works pretty well most of the time.  If you have no problems playing wma's in totem, you could also try /usr/bin/totem as the command.  The nice thing is you don't have to restart Firefox each time.  Just try the different player and re click.

Good Luck.Great suggestion. However, I tried and it still won't play in either VLC or totem. VLC seems to start loading the file but nothing ever happens and totem gives the same message as it did before. 

I am able to play wma files in both vlc and totem from the desktop though.

---

### Post by vol_freak on 2007-02-04
Wow, I got it to work suddenly. Using that plugin I right-clicked on the filmstrip looking icon and clicked on MediaPlayerConnectivity >> open *file* (which shows an asp file for some reason). 

Weird that it works that way. 

Thank you so much!!

---

