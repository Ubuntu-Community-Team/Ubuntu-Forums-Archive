---
title: "Gnome-Shell Buggy"
date: 2013-05-10
forum: General Help
---

### Post by MaZaMo on 2013-05-10
I have Ubuntu 13.04. I tried installing gnome shell without any of the added programs (sudo apt-get install gnome-shell), but it's really buggy so i ended up removing it. When you first logged in to gnome shell the top desktop icon would only be partially visable because half of it stuck under the top bar. When I opened any application it would correct itself. But when the activites is open the desktop icons still show up too and it's really annoying as it gets in the way. I would like to have gnome shell but not if there isn't a way to fix these (there were other annoying bugs but those two are the worst).

---

### Post by MaZaMo on 2013-05-10
Also I have tried upgrading to gnome shell 3.8 ([http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome)) but after adding the repository and updating (even before installing), my wallpaper went white and I couldn't change it so I had to reinstall Ubuntu. What is this from and how do I prevent it if I want gnome 3.8??? I don't care for 3.6

---

### Post by MaZaMo on 2013-05-10
What do I do?

---

### Post by markbl on 2013-05-11
From a clean 13.04 Ubuntu install, just
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell gnome-tweak-tool

```

Don't install ubuntu-gnome-desktop or the staging ppa as described in that article. Reboot and log into gnome shell. Run tweak took and disable "have file manager manage the desktop". You should get your desktop background back then.

You don't really want icons and stuff on your desktop anyhow, as I argued from [here](http://ubuntuforums.org/showthread.php?t=2130575&page=2&p=12619804#post12619804).

Actually I suspect you may even be able to use the file manager for the desktop if you install ubuntu-gnome-desktop but I have not tried it because I don't want the file manager, and also I **much** prefer the default Ubuntu Ambiance theme and font etc for gnome shell in preference to the standard gnome theme and fonts.

---

### Post by MaZaMo on 2013-05-11
Ignore my second comment about wanting gnome shell 3.8. I'm fine with 3.6. But what if I wanted desktop icons? They still all show up in activities.

---

### Post by hmandmpsaunders on 2013-05-12
What I do is to copy the desktop configuration file from /usr/share/applications to /home/../desktop.  Seems to work.

---

