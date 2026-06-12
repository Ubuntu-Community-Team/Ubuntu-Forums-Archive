---
title: "Ubuntu 16.04 upgrade - Folding@Home python error"
date: 2016-04-30
forum: General Help
---

### Post by jon_williams on 2016-04-30
I've just upgraded one of my machines to 16.04, and now on installing Folding@Home (which I run on many Ubuntu machines, though all the others pre-16.04 at the moment), I get a python error.
Anyone else had the same issue?
Anyone know a fix?

---

### Post by khowe on 2016-05-01
Here is what worked for me.

I found the file here:
[https://launchpad.net/ubuntu/xenial/amd64/python-support/1.0.15](https://launchpad.net/ubuntu/xenial/amd64/python-support/1.0.15)

wget [http://launchpadlibrarian.net/109052632/python-support_1.0.15_all.deb](http://launchpadlibrarian.net/109052632/python-support_1.0.15_all.deb)
sudo dpkg -i python-support_1.0.15_all.deb

Not sure why it doesn't install automatically, maybe a bug report is in order.

---

### Post by jon_williams on 2016-05-01
Works for me too. Thanks very much :D

---

### Post by jon_williams on 2016-05-02
Since Ubuntu have a Folding team, "TeamUbuntu", I would have thought that someone on the team would have raised the issue and filed a bug report ... but, perhaps not.

---

### Post by Bucky Ball on 2016-05-02
*Thread moved to **General Help**.*

Reason: *Installations and Upgrades* is for problems installing and upgrading the OS, not apps. ;)

Glad you got it fixed. Please mark the thread as solved to help others.

---

