---
title: "Mono Problems"
date: 2005-05-08
forum: General Help
---

### Post by harryc on 2005-05-08
I have installed Beagle 0.9 and Mono 1.?.? using the Beagle/Ubuntu wiki.

[http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)

It dumped what appears to be Mono 1.0.5-1 onto my machine. It is supposed to install Mono 1.1.6 (unless the .deb package names are confusing me). I added the backports to my apt sources.list as described in the wiki. 

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted
deb [http://manno.name/debian/](http://manno.name/debian/) breezy cvs

I otherwise followed it word for word. Beagle runs but in debug mode it is throwing up some errors that point to a downlevel mono. How do I get from 1.0.5-1 to the 1.1.6 in hoary-backports? Apt tells me there are no upgrades available...and yes I did an apt-get update. 

[http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/)

---

### Post by harryc on 2005-05-09
Please disregard. I downloaded and installed all of the mono 1.1.6 packages manually. Slow, but effectice. If anyone knows why apt didn't pickup the latest versions originally, please let me know. Should I have commented out everything in apt/sources.list except for the following?

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted
deb [http://manno.name/debian/](http://manno.name/debian/) breezy cvs

---

### Post by tread on 2005-05-09
As far as I know, apt should have picked up the latest version. You wouldn't have done any version pinning now, would you? 

That's the only solution I can think of .. but I am fairly new at debian-based installations :).

---

