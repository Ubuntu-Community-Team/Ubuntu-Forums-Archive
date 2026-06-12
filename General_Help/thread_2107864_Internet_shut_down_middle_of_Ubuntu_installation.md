---
title: "Internet shut down middle of Ubuntu installation"
date: 2013-01-22
forum: General Help
---

### Post by wintoys on 2013-01-22
So internet broke down middle of installation of ubuntu while it was downloading updates. Is this bad or should i reinstall ubuntu. However installer just went to end and it seems ok, i haven't seen any problems yet except freezing of screen time to time but i am not sure if it has come always with ubuntu.

Is it ok or do i have to reinstall everything. Do it just automatically skip updates or do it affect someway quality of install?

---

### Post by plucky on 2013-01-23
> **wintoys said:**
> So internet broke down middle of installation of ubuntu while it was downloading updates. Is this bad or should i reinstall ubuntu. However installer just went to end and it seems ok, i haven't seen any problems yet except freezing of screen time to time but i am not sure if it has come always with ubuntu.

Is it ok or do i have to reinstall everything. Do it just automatically skip updates or do it affect someway quality of install?

You don't need the internet to be **on** to install from USB/CD.

Just open a terminal and run ```
sudo apt-get update
sudo apt-get dist-upgrade
``` and the system will download and install the latest updates.

Good Luck

---

