---
title: "a firefox problem"
date: 2005-09-30
forum: General Help
---

### Post by dphipps on 2005-09-30
In my system there is a package firefox and package mozilla-firefox.  I updated my system and it trys to upgrade nozilla-firefox but fails saying this (E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox).  It won't let me remove package fireox without upgrading mozilla-firefox and won't lit me upgrade mozilla-firefox without first removing firefox.  Can anyone help me?

---

### Post by heimo on 2005-09-30
Are you sure you're using Hoary and not Breezy? If yes, where did you get firefox-package? If you're using Breezy, you can uninstall [mozilla-firefox ]("http://packages.ubuntu.com/breezy/devel/mozilla-firefox")and leave firefox-package.

---

### Post by dphipps on 2005-09-30
I thought about unistalling mozilla-firefox put it wants to unistall ubuntu-desktop at the same time.

---

### Post by aysiu on 2005-09-30
When I go into Synaptic, [Mozilla-Firefox](http://i22.photobucket.com/albums/b337/psychocats/8db97849.png) appears as just a transitional package to Firefox[/url]

---

### Post by heimo on 2005-09-30
Yes, mozilla-firefox is transitional package - at least in Breezy. And ubuntu-desktop is metapackage that can be removed safely (just make sure you reinstall it before dist-upgrading - upgrading to Breezy for instance).

---

