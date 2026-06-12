---
title: "What happened to the MythTV repository?"
date: 2005-08-23
forum: General Help
---

### Post by fromans4 on 2005-08-23
I am attempting a fresh install of MythTV on Ubuntu 5.04. I have my system installed and all pre-requisites done. As per previous installations, I added "deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) unstable myth" to my repositories list. When I attempt to install any of the MythTV components, I get errors saying that Mythfrontend & Mythbackend need to be installed but will not be??? Does anyone know if there is a problem with this repo? I have used it in the past, but its been awhile.

BTW - If I open up YUMEX I can see all of the current MythTV components listed. I have also browsed to the repo site and checked through the myth repo's manually and everything seems to be there. I don't know of any other repository I can use to get the current build. The Ubuntu backports only have v17.1 available.

Any help would be appriciated,
Brent

---

### Post by Chareos on 2005-08-28
0.18.1 depends on... too recent packages.
Hoary doesn't match those dependancies.

Adding a lot of unofficial/unstable/testing repositories would make me install myth 0.18.1 but I feel not so comfortable replacing half of my ubuntu desktop with non rock-stable ones.

I tried to compile 0.18.1 manually but it don't senses my up and working lirc... so now I'm fallen back to 0.17 - which is on ubuntu dependancies and has lirc already built in.

---

