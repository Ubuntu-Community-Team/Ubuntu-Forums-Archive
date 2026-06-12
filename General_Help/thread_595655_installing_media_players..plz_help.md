---
title: "installing media players..plz help"
date: 2007-10-29
forum: General Help
---

### Post by thousandpimps on 2007-10-29
i'm new to ubuntu 7.10 and iam getting really frustrated because i cannot seem to install media players...

i want to install amarok for audio player but the site said to add multiverse and universe repositories which i dont know how to
 also i want to install mplayer vlc and xion but i know ill get stuck somewhere so iam not even trying

can any one please give me specific instructions on howto install these softwares

thanks a lot
ubuntu rocks

---

### Post by Jbs63 on 2007-10-29
just use apt-get.. its relativly simple..
For vlc: sudo apt-get install vlc
amarok: sudo apt-get install amarok

all you have to do is type in a password and it installs itself.. you need the internet though :P

---

### Post by notatoad on 2007-10-29
to add repositories (universe, multiverse) go to system>administration>software sources and check them off.  you shouldn't need to do this for amarok and vlc though.

just go to applications>add/remove OR system>administration>synaptic and search for what you want.

alternatively type "sudo apt-get install amarok vlc" into a terminal window.

for future reference step by step instructions for installing just about any program is available at [www.ubuntuguide,org](www.ubuntuguide,org).  that was a big help to me when i first installed ubuntu, and is still almost a daily reference.\

also, on the websites for most of the software, you can get installers packaged as .deb files.  you can install these the same way you do with a windows installer (double click and let it go) but this is the least desirable method as it does not add the correct repositories for automatic updates (i think?).

---

