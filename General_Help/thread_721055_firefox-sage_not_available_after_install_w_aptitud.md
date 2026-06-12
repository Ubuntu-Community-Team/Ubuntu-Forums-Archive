---
title: "firefox-sage not available after install w/ aptitude"
date: 2008-03-10
forum: General Help
---

### Post by farruinn on 2008-03-10
The [Sage]("http://sage.mozdev.org") module isn't loaded into after installing it with `sudo aptitude install firefox-sage'. Any ideas? Here's what the package installed:

```
$ dpkg -L firefox-sage
/.
/usr
/usr/share
/usr/share/mozilla-extensions
/usr/share/mozilla-extensions/sage
/usr/share/mozilla-extensions/sage/chrome
/usr/share/mozilla-extensions/sage/chrome/sage.jar
/usr/share/mozilla-extensions/sage/install.rdf
/usr/share/mozilla-extensions/sage/chrome.manifest
/usr/share/mozilla-extensions/sage/uninstall
/usr/share/mozilla-extensions/sage/uninstall/Uninstall
/usr/share/doc
/usr/share/doc/firefox-sage
/usr/share/doc/firefox-sage/MPL-1.1.txt
/usr/share/doc/firefox-sage/copyright
/usr/share/doc/firefox-sage/changelog.Debian.gz
/usr/lib
/usr/lib/iceweasel
/usr/lib/iceweasel/extensions
/usr/lib/iceweasel/extensions/{a6ca9b3b-5e52-4f47-85d8-cca35bb57596}

```

---

