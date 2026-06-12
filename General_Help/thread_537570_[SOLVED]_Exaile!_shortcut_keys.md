---
title: "[SOLVED] Exaile! shortcut keys"
date: 2007-08-29
forum: General Help
---

### Post by bogdan_5844 on 2007-08-29
can i make global key shortcuts in Exaile! for the play/pause,next,previous functions?i know that in Amarok they are as in winamp with WinKey e.g. Win+Z-Previous Track
Win+X-Play,etc.

---

### Post by forestpixie on 2007-08-29
Open exaile - edit plugins and add the global hotkeys plugin

---

### Post by bogdan_5844 on 2007-08-29
in Tools->Plugins i have only Serpentine,Stream Ripper,Mini Mode,and a few others,but none has the name Global Hotkeys ...how do I add it?

---

### Post by forestpixie on 2007-08-29
what version are you using - I might have had to upgrade to get the plugin 2.10 - if you're on a lower version you can get the download [here]("http://www.exaile.org/downloads"). Install that if necessary then look again for plugins.

It should be in available plugins in the edit plugins windows

---

### Post by bogdan_5844 on 2007-08-29
0.2.8 is my version,i will upgrade :P see if that solves it

Back with 0.2.10,when i go in the plugins page it has none installed,on available plugins tab i get a "No plugins available for your version"error :(

---

### Post by forestpixie on 2007-08-29
We'll try adding the exaile repo then

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak.2908
```

open the file to edit it (I assume you're using Ubuntu, if not use the text editor instead of gedit)

```
gksudo gedit /etc/apt/sources.list
```

go to very end of list add this
```
deb http://download.tuxfamily.org/syzygy42 feisty exaile
```

save and close

then do these in terminal separately

```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg
sudo apt-key add 8434D43A.gpg
sudo apt-get update
sudo apt-get upgrade
```

then have another look for the plugins -

---

### Post by forestpixie on 2007-08-29
Have to say this is all really odd - I had exiale as I'd had some problems with amarok.
As I'm not using it now I purged it ands reinstalled - now I can't get the plugin either. I will have to dig around a bit unless someone else comes along with an answer.

---

### Post by bogdan_5844 on 2007-08-29
yep...i think that is something wrong with the package?:confused: it still does the same thing... :(

---

### Post by forestpixie on 2007-08-29
emmm.. like I said I will have a dig about to see if I can get it working today - will post here if I can

in the meantime if you find out you can help me :)

just glad I use amarok - it took me a while to get the exail plugin working in the first place, you'd think it would be part of the package really

---

### Post by bogdan_5844 on 2007-08-29
hey,i managed to do it trough the Keyboard Shortcuts menu :P (i uninstalled Rythmbox because i don't use that thing

---

### Post by forestpixie on 2007-08-29
ok - cool - mark this as solved please - i will carry on looking to see if I can sort the plugin situation

---

### Post by bogdan_5844 on 2007-08-29
ok,thanks for help ):P

*Thread Solved*

---

### Post by soxs on 2007-08-29
Add the svn repo frome [www.exaile.org](www.exaile.org) to your repos (detailed info can be found there aswell).
(Make sure to purge ALL artifacts from older exaile versions)

Global hotkeys plugin works for me as a charm.^^

---

### Post by forestpixie on 2007-08-29
that did it again - can't for the life of me remember where I got the hotplug from in the first place.

---

