---
title: "Mplayer Codecs where to?"
date: 2005-04-16
forum: General Help
---

### Post by jaquesdp on 2005-04-16
Hi there all. i want to install the essentials codecs for mplayer to be able to play wmv and wmv 9 files. i cant find the codecs folder for mplayer to install the codecs to?

Any help please..

---

### Post by jhands on 2005-04-16
add the extra repositories

and then do:
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

---

### Post by Bob D. on 2005-04-16
Easiest way is to install the .deb from Hoary Backports: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

The codecs are in hoary-extras-restricted. Just following the instructions on the main page to add these repos to your sources.list.

Bob

---

