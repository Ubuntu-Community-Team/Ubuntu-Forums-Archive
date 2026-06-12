---
title: "Problem upgrading firefox to 1.0.7"
date: 2005-09-23
forum: General Help
---

### Post by domstyledesign on 2005-09-23
I've encountered this problem when trying to upgrade firefox via synaptic

```
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
```

any ideas?

---

### Post by aysiu on 2005-09-23
It'll be easier for people to help you troubleshoot if you post your /etc/apt/sources.list and the output of these terminal commands ```
sudo apt-get update
sudo apt-get install mozilla-firefox
```

---

### Post by phex on 2005-09-23
I would suggest, that you deinstall firefox-gnome-support, mozilla-firefox-gnome-support and mozilla-firefox. after that you can simple install the deinstalled packages again with the new version number. ;) your settings and bookmarks of firefox should not be deleted if you do it this way. 
Anyway, if you wnat to be on the save side, simple rename the  .mozilla directory in you home directory(~) to .mozilla.save and after reinstallation do it the reverse. hope that will help you.

---

### Post by Prefader on 2005-09-23
####Edit####
What Phex said.  :P

Also, I used the "complete removal" option on the package "firefox", and I still have my extensions, bookmarks, etc.  Go figure.  :)

####

I was able to get the update installed by following these steps in Synaptic:

1) Mark for COMPLETE REMOVAL the package "Firefox".  This will also mark for removal :  Firefox-gnome-support, yelp, mozilla-firefox, mozilla-firefox-gnome-support, ubuntu-desktop, and maybe mplayer-mozilla (if installed).
2) Apply.
3) go back into synaptic.  Select the packages : mozilla-firefox, ubuntu-desktop, yelp, and mozilla-firefox-gnome-support. I *think* that tese will all be auto selected when you select mozilla-firefox, but just in case, check hem all and verify that they're marked for installation.
4) apply
5) restart system.  <--why?  dunno.  Someone may know of a better way to do this.

I'm positive that this will all work with apt-get as well (just "apt-get remove" the packages, then "apt-get install" them), but synaptic is where I think a lot of people are more comfortable.

Hope this helps.

---

### Post by Wide on 2005-09-23
[QUOTE=Prefader]####Edit####
What Phex said.  :P

Also, I used the "complete removal" option on the package "firefox", and I still have my extensions, bookmarks, etc.  Go figure.  :)

####

I was able to get the update installed by following these steps in Synaptic:

1) Mark for COMPLETE REMOVAL the package "Firefox".  This will also mark for removal :  Firefox-gnome-support, yelp, mozilla-firefox, mozilla-firefox-gnome-support, ubuntu-desktop, and maybe mplayer-mozilla (if installed).
2) Apply.
3) go back into synaptic.  Select the packages : mozilla-firefox, ubuntu-desktop, yelp, and mozilla-firefox-gnome-support. I *think* that tese will all be auto selected when you select mozilla-firefox, but just in case, check hem all and verify that they're marked for installation.
4) apply
5) restart system.  <--why?  dunno.  Someone may know of a better way to do this.

I'm positive that this will all work with apt-get as well (just "apt-get remove" the packages, then "apt-get install" them), but synaptic is where I think a lot of people are more comfortable.

Hope this helps.[/QUOTE]



I have two installs tried both of your methoeds & works like a charm

I am using the extra resp found at Ubuntuguide

Thanks & good luck all :)

---

