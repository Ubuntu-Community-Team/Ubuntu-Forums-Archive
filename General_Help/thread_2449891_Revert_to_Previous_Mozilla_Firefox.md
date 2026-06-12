---
title: "Revert to Previous Mozilla Firefox"
date: 2020-09-03
forum: General Help
---

### Post by UserJB on 2020-09-03
I'm running Ubuntu 16.04.  A few weeks ago,an update installed a new version of Mozilla Firefox: 80.0.  This version crashes every 10 minutes.  How can I revert to a previous version?  I'd like to do it through the apt tools.

---

### Post by walts48 on 2020-09-04
> **UserJB said:**
> I'm running Ubuntu 16.04.  A few weeks ago,an update installed a new version of Mozilla Firefox: 80.0.  This version crashes every 10 minutes.  How can I revert to a previous version?  I'd like to do it through the apt tools.

Can't help, but Mozilla recently released an update to 80.0.1 that Ubuntu should pick up.

Fixes a crash problem.

[https://www.mozilla.org/en-US/firefox/80.0.1/releasenotes/](https://www.mozilla.org/en-US/firefox/80.0.1/releasenotes/)

Do you get the crash reporter and submit reports to Mozilla?

---

### Post by Impavidus on 2020-09-04
There's no revert built-in, except for the kernel. The Firefox that came with the original release of Ubuntu 16.04 should still be available from the xenial/main repository (Firefox 80 comes from the xenial-updates/main repository), but that version must by now be ancient. It may be possible to grab a version from a livedisk or, with some luck, the previous version of Firefox may still be in your package cache (/var/cache/apt/archives/firefox*).

But it would be much better to upgrade to a version where this bug is fixed.

---

### Post by mikewhatever on 2020-09-04
You may just want to uninstall the new Firefox, and use "firefox-esr" from this PPA: [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa).
The ESR version has less changes, and should work better on an old OS.
PS: It is time to upgrade.

---

### Post by Dennis N on 2020-09-04
You can download most past Firefox releases from the official Mozilla archive:
[https://ftp.mozilla.org/pub/firefox/releases/](https://ftp.mozilla.org/pub/firefox/releases/)
installation with a package manager is not necessary for these.

---

### Post by Impavidus on 2020-09-05
> **walts48 said:**
> Can't help, but Mozilla recently released an update to 80.0.1 that Ubuntu should pick up.

Ubuntu picked it up. I just installed 80.0.1 from the repositories. That may be the simplest way to solve the problem.

---

