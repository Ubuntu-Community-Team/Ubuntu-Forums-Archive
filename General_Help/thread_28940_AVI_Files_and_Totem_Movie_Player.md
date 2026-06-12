---
title: "AVI Files and Totem Movie Player"
date: 2005-04-22
forum: General Help
---

### Post by JACIE on 2005-04-22
Hi,

reasonably new to Linux/Ubuntu so sorry if this is very basic.

I'm trying to view an AVI file using the Totem Move Player. At present I am only getting audio but no video, just a blank screen.

Any ideas?

Many thanks - JC

---

### Post by Leif on 2005-04-22
You probably need to follow the steps here (and maybe some of the ones below it):

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by JACIE on 2005-04-22
[QUOTE=Leif]You probably need to follow the steps here (and maybe some of the ones below it):

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)[/QUOTE]
 Leif,

many thanks for that. Had to add extra repositories for the w32codecs as per:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by nigel on 2005-04-24
Hey all 

I am having the same problem, i've installed the following

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install xine-ui

but still only sound, is there something I am missing, is there some other thing i need to download

whoops posted this in te wrong place --- I'm using warty warthog version

---

