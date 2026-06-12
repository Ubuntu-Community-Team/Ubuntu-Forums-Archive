---
title: "After fresh ubuntu 18.04 installation - update / upgrade is just timing out in-betwee"
date: 2019-06-20
forum: General Help
---

### Post by sudhirdhumal89 on 2019-06-20
Tried twice to install fresh Ubuntu 18.04.1. Every time I try to install updates / or upgrades for packages it just times out.
Just to make sure that I have good internet connection I thought to download few software packages and they were getting downloaded at the speed to 2 MB/s (from other sites) but when I tried to use apt dist-upgrade command it just keep waiting for the ubuntu server. Really fade-up. Trying to update from last 30 min (apt update). apt dist-upgrade is even worse running from last 1 hr. Not even utilizing 1% of my network bandwidth.

---

### Post by Geoffrey_Arndt on 2019-06-20
Seems updater process not working here also.    Major kernel updates & thunderbird just will not complete.   I've tried to change mirror servers to get fastest connection . . . updates are just not completing.   May be some issues at Canonical source?

UPDATE:   all normal again . . . was a network outage at ISP.

---

### Post by cruzer001 on 2019-06-20
The command is:

sudo apt-get dist-upgrade

If using just apt:

sudo apt full-upgrade

---

