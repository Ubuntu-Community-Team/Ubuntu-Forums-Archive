---
title: "How do I install the official BitTorrent .deb?"
date: 2006-12-11
forum: General Help
---

### Post by LAurel on 2006-12-11
I noticed the *bittorrent* package that comes with Ubuntu 6.10 is *3.4.2*, while the latest version on bittorrent.com is [*5.0.3*](http://download.bittorrent.com/dl/bittorrent_5.0.3_python2.4.deb).

I downloaded the [*official .deb*](http://download.bittorrent.com/dl/bittorrent_5.0.3_python2.4.deb), but GDebi reports a conflict with the *3.4.2* package already in Ubuntu.

Now, I have the following problem: when I try to uninstall the *3.4.2* package in Synaptic, I notice I can **only** do so by also uninstalling the *ubuntu-desktop* package, which, according to its own description, should not be removed.

Is there any way I can install the *5.0.3* .deb on my system without causing problems?

---

### Post by daller on 2006-12-11
The times I've run into these problems (well, that was with kubuntu-desktop) I simply asked it to remove it, and I reinstalled it afterwards...

Removing the 3.4.2 version, should enable you to install the newest version.

---

### Post by Delkster on 2006-12-11
> **LAurel said:**
> Now, I have the following problem: when I try to uninstall the *3.4.2* package in Synaptic, I notice I can **only** do so by also uninstalling the *ubuntu-desktop* package, which, according to its own description, should not be removed.

Uninstalling ubuntu-desktop is safe and doesn't directly remove any functionality from the system. If you do remove it, you should reinstall it before upgrading the system to a new release, though. Ubuntu-desktop is a so-called metapackage that doesn't contain any actual applications in itself but instead it's set to be dependent on everything that belongs to the default Ubuntu desktop, so by having that installed you can make sure that you have everything that belongs to the default setup.

---

### Post by LAurel on 2006-12-11
Thank you both :) .

I didn't know what uninstalling *ubuntu-desktop* would do to my system, but everything works great now.

---

