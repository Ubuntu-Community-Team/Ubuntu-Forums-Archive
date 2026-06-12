---
title: "Firefox Crashes and WONT upgrade or un-install"
date: 2005-07-28
forum: General Help
---

### Post by SynapseR on 2005-07-28
Hi,
After upgrading firefox via the update manager, it now fails to open when I launch it.
There are 2 updates related to it :

mozilla-firefox & mozilla-firefox-gnome-support (1.0.6) which fail to update

I also can't un-install or downgrade firefox.

Here is the error message :

E: /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.6-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Help Please ........

--
SynapseR

---

### Post by mad_scientist03 on 2005-07-28
One quick way to get Firefox working is to download the tarball (.tar.gz file) from the Firefox website, extract it into your home directory, and then just './~/firefox-install/firefox' from the terminal to use Firefox.

Another option is to completely remove the Firefox packages, and the relevant config files/directories in your home directory, and re-install those packages.

---

