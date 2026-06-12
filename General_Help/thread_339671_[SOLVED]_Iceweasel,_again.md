---
title: "[SOLVED] Iceweasel, again"
date: 2007-01-16
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-01-16
Hi every one. Last year I tried Iceweasel and I liked  but then I switched to another browser. I would like to go back to Iceweasel but I am having trouble with following the wiki page (silly me) I am also running Xubuntu if that helps any one that is gonna take on this task. Can some one please provide me with a nice little how to for me to copy/paste in the terminal, no questions asked :)  I thought I had seen a package in synaptic but I do not see it now. I would really appreciate help on this, Sally:confused: :-?

---

### Post by bionnaki on 2007-01-16
I thought mozilla & debian are friends again...so iceweasel isnt used anymore. I could be wrong.

---

### Post by IusedTObeSOMEONEelse on 2007-01-16
I have been using swiftfox and really like the response I get out of it. I have even been steering people to use it, bvut due to personal issues I would like to try Iceweasel again and see if it responds as well as Swiftfox:)

---

### Post by IusedTObeSOMEONEelse on 2007-01-16
Bump :evil:

---

### Post by ChrisNiemy on 2007-03-01
Hi!

I also switched to Iceweasel because of the Debian patches. Just was bored and now I'm happy with it. On the wiki page [InstallIceweasel]("http://wiki.ubuntu.com/InstallIceweasel") you need to add the debian unstable repository to your /etc/apt/sources.list (just once while installing, remove it otherwise).

And probably due dependency issues you will have to remove (NOT purge, to keep your configs in ~/.mozilla) the ubuntu packages firefox, firefox-gnome-support etc and yelp.

I'm wonderin why the GNU guys aren't updating Iceweasel from 1.5.0.9 to 2.0.0.2. Because this .tar.gz is far more easier to install then the debian unstable package. However the debian unstable package is 2.0.0.2.

Try also this link: [http://www.ubuntuforums.org/showthread.php?t=270631&highlight=iceweasel](http://www.ubuntuforums.org/showthread.php?t=270631&highlight=iceweasel)

---

