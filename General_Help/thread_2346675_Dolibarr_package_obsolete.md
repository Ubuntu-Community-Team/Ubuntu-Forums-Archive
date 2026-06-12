---
title: "Dolibarr package obsolete"
date: 2016-12-17
forum: General Help
---

### Post by Wolfsbane on 2016-12-17
Hi,

Not at all sure where to post this.
I noticed that the dolibarr package you get through apt install is very old. It's 3.5.8 while the upstream version is now up 4.0.2 if I remember correctly. This is problematic because 3.5.8 has a serious bug in relation to newer versions of both MySQL and PHP (basically it's uninstallable according to this bug report: [https://github.com/Dolibarr/dolibarr/issues/4755](https://github.com/Dolibarr/dolibarr/issues/4755)) and also Dolibarr 4.x is supposed to be compatible with PHP7.

How do I get the package updated? Anyone maintaining the dolibarr package?

---

### Post by howefield on 2016-12-17
The newer version (4.0.2) is available in the current development release so will be included on release April 2017 but nothing earlier.

Guess you could try the Ubuntu developers mailing list ?

---

### Post by Wolfsbane on 2016-12-17
Ah I see, I'll give it a try - thanks.
On principle is it possible to download a dev package and make it install in an older version respecting already possibly installed requisits?

---

### Post by howefield on 2016-12-17
> **Wolfsbane said:**
> On principle is it possible to download a dev package and make it install in an older version respecting already possibly installed requisits?

Absolutely possible.

The package can be downloaded from [http://packages.ubuntu.com/search?suite=zesty&keywords=dolibarr](http://packages.ubuntu.com/search?suite=zesty&keywords=dolibarr) and you can check the dependencies from there.

Obviously I have to say that doing so would be out of the norm and not necessarily be a wise thing to do, it would be on you and if you break anything you get to keep all the pieces ;) Perhaps installing with apt using the -s option to simulate an install would give you an idea of whether it would work (after you have checked the dependencies)

---

### Post by howefield on 2016-12-17
Should also add that there may be a trustworthy PPA that you could use.

I haven't looked but searching for something like "dolibarr ppa" should return anything useful.

---

### Post by ian-weisser on 2016-12-17
> **Wolfsbane said:**
> 3.5.8 has a serious bug in relation to newer versions of both MySQL and PHP (basically it's uninstallable according to this bug report: [https://github.com/Dolibarr/dolibarr/issues/4755](https://github.com/Dolibarr/dolibarr/issues/4755) 

If you can show that the bug is fixed in 4.0.2 running on Ubuntu 14.04 and 16.04, then it's eligible for a [Stable Release Upgrade]("https://wiki.ubuntu.com/StableReleaseUpdates") . File a bug against [Dolibarr in Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/dolibarr"), and follow the SRU instructions.

The SRU team won't do everything automatically, there are lots of SRUs. Dolibarr users must work together to make it easy and obvious for the SRU to be approved quickly.

If the SRU is denied, updated versions of Dolibarr can still be [backported]("https://wiki.ubuntu.com/UbuntuBackports") to older releases of Ubuntu.

Most new packages, including Dolibarr, are imported regularly from Debian. If you are interested in seeing newer releases of Dolibarr packaged for Debian and Ubuntu more frequently, contact the Debian maintainer (sudo apt show dolibarr | grep Original-Maintainer) and offer to help.

Outside of the apt ecosystem, contributors are also welcome to snappify software. A Dolibarr snap can be updated any time the maintainer wishes...like immediately upon new releases.

---

