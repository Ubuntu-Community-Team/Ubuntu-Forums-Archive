---
title: "Trouble installing BasKet notes on Gutsy"
date: 2008-02-28
forum: General Help
---

### Post by Derrelicte on 2008-02-28
[img]http://img521.imageshack.us/img521/8313/screenshotsynapticih3.png[/img]

I'm trying to install Basket and this error message comes up.

I've tried a sudo apt-get -f install to see if it would pick anything up that was messed up and it found nothing.

Checking under Custom Filters > Broken in Synaptics brings up nothing.

All Ubuntu updates have been installed.

I know that it can install, as I've done it on another laptop running Ubuntu.

---

### Post by pointone on 2008-02-28
Make sure the CD-ROM source is commented out/disabled in your /etc/apt/sources.list.

---

### Post by Derrelicte on 2008-02-28
I have it disabled and it's still giving me the same error message.

---

### Post by Derrelicte on 2008-02-28
I don't know if this helps any, but doing a sudo apt-get install basket brings up the following error message:

The following packages have unmet dependencies:
  basket: Depends: kdelibs4c2a (>= 4:3.5.7-1) but it is not going to be installed
          Depends: kontact (>= 4:3.5.7enterprise20070926) but it is not going to be installed
          Depends: libgpgme11 (>= 1.0.1) but it is not installable
          Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but it is not going to be installed
E: Broken packages

---

### Post by Derrelicte on 2008-02-28
> **pointone said:**
> Make sure the CD-ROM source is commented out/disabled in your /etc/apt/sources.list.

This got me thinking about the repositories, and I ended up enabling all the repositories.  It installed more stuff and it installed fine.

Thanks

---

