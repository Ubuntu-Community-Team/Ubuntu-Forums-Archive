---
title: "Gnome Do won't install"
date: 2008-03-13
forum: General Help
---

### Post by iThinkergoiMac on 2008-03-13
I found a program called Gnome Do and it looks amazing. It's essentially a clone of Quicksilver for Mac OS X, which I've missed a lot since I got my IBM ThinkPad from school. I went to install it from the repositories for Gutsy... and it's not there. What gives?

Anybody have any idea if I'm going something wrong or if it's not up? And if it's not, where I could get it? Thanks!

And, yes, I did add the correct repositories to the sources.list file. Even shows up in Synaptics.

---

### Post by forestpixie on 2008-03-13
how you installing it - or trying to?

---

### Post by iThinkergoiMac on 2008-03-13
sudo apt-get install gnome-do

Also, I tried searching for it in the Synaptic Package Manager, but it couldn't find it either.

---

### Post by forestpixie on 2008-03-13
well I'd check you sources list again then - because it's definitely there

apt-cache search gnome-do
gnome-doc-utils - a collection of documentation utilities for the Gnome project
gnome-doc-tools - Tools, stylesheets and DTDs for GNOME.
gnome-do - Quickly perform actions on your desktop

make sure your sources are correct to 

deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) gutsy main

---

### Post by iThinkergoiMac on 2008-03-13
Odd... that source wasn't the one I was seeing on multiple pages telling me how to find it. But it works... and it's installing now. Thanks!

---

### Post by Perpetual on 2008-03-13
The [Wiki]("https://wiki.ubuntu.com/GnomeDo/Installation") will answer most of your questions.

Landon.

---

