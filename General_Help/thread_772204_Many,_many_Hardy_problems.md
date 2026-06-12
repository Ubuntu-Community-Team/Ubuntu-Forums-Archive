---
title: "Many, many Hardy problems"
date: 2008-04-28
forum: General Help
---

### Post by acl123 on 2008-04-28
I know there is already a glut of Hardy threads, so I apologise in advance. Rather than starting new threads for all of these at this stage I thought I would just put them in one post for now. I've only been working on it this afternoon, so I know that it usually takes a couple of days to iron out everything.

The following are problems I've noticed after upgrade from Gutsy (7.10) to Hardy (8.04).


**GRAPHICS**
*  Working xorg.conf replaced with not-working xorg.conf, which meant my resolution was all messed up. I replaced the one Hardy made with the backup, which fixed my resolution, but I'm not sure why it was replaced in the first place.

*  NVidia accelerated graphics doesn't work. If I start Ubuntu with it enabled, it starts in low graphics mode. Tried using EnvyNG. Tried reinstalling using "sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall" command

*  Google Earth doesn't work, obviously because 3d acceleration is not working... but instead of crashing gracefully it causes Gnome to reset (it instantly logs out and I end up on the login screen).


**PERFORMANCE**
*  On numerous occasions the mouse slows down and becomes jittery. There doesn't appear to be anyway to get it back to normal other than a full reset... even (Ctrl-Alt-Backspace doesn't help).

*  On one occasion I couldn't open any programs. Whenever I clicked on any program, even a terminal, it would hang for a while and then do nothing.


**FIREFOX**
*  Half my extensions didn't work, some of them quite important like Foxmarks. Also I believe the performance issue above may have been caused by Firefox. So I uninstalled it and went back to Firefox 2... [Edit: This appears to be a problem not with performance, but with the mouse, because when I unplug it and plug it back in again it works]

*  But now I can't re-enable any of my extensions  or themes now in Firefox 2 - the "Enable" button just does nothing. I click on it and nothing happens.

*  Firefox 2 has also crashed once on me, for no apparent reason, bringing down the rest of Ubuntu with it (had to hard reset).

**SOUND**
*  XMMS is gone...

*  So I switched to Audacious but Audacious keeps hanging and I can't find out how to add a whole directory of songs to the playlist. I think this is why I never switched to Audacious before.


**WIRELESS**
*  Seems to be generally working this time although it has dropped out on two occasions (had to reset to get it back again). It doesn't usually just drop out like that, so at this stage Ubuntu looks like the culprit.


**AND OTHER WEIRD THINGS...**
*  One time when I logged in to Gnome it gave me an error message along the lines of "There was an error starting the GNOME Settings Daemon." I had to do a hard reset, but I haven't seen the error again.

* Memaid doesn't work anymore. I know its not supported but I still liked it better than Mnemosyne.

---

