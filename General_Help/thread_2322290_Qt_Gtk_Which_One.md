---
title: "Qt? Gtk? Which One"
date: 2016-04-27
forum: General Help
---

### Post by echotech2 on 2016-04-27
Ubuntu 16.04 - Unity (fresh install)

  Using Synaptic Package Manager, some programs have a -qt AND a -gtk version. Which should I use if I want to install one of these programs?

  Oops, probably wrong forum.

---

### Post by vasa1 on 2016-04-27
Can you please provide some examples?

---

### Post by ajgreeny on 2016-04-27
Just in case you are unaware of this the qt and gtk libraries are those generally used for building packages for KDE (qt) and gnome based (gtk) DE applications respectively, but not exclusively.  This tends to give the applications the appropriate look for the DE you run.

I suspect that for the unity desktop you would normally use the gtk version, and if you choose the qt version you may find that a lot of qt libraries would also be needed as dependencies.  You can, however, install any package from the repos into any of the DE versions of *ubuntu.

As vasa1 says, give us some examples of what you want to install and we can probably help you in more detail.

---

### Post by vasa1 on 2016-04-27
[s]BTW, these harmless commands (because of *-s*) will tell a user which qt4 and qt5 packages / dependencies are already present:
```
apt-get remove -s libqt4* | grep Remv | cut -d ' ' -f -2
apt-get remove -s libqt5* | grep Remv | cut -d ' ' -f -2
```[/s]

I scratched that because the first command listed *audacity*. But I don't see any *qt* depends for *audacity* :confused:

---

### Post by echotech2 on 2016-04-27
I'll mark this solved.  There was no particular package, I just noticed it scrolling through Synaptic and was curious.  Thanks for the info.

---

