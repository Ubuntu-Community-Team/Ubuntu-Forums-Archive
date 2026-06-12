---
title: "Skype not upgrading"
date: 2013-06-02
forum: General Help
---

### Post by jockyburns on 2013-06-02
Tried to upgrade Skype today, but it won't upgrade. Here's the message I get

> dpkg: considering removing skype-bin in favour of skype ...dpkg: no, cannot proceed with removal of skype-bin (--auto-deconfigure will help):
 skype depends on skype-bin
  skype-bin is to be removed.
dpkg: regarding .../skype-ubuntu-precise_4.2.0.11-1_i386.deb containing skype:
 skype conflicts with skype-bin
  skype-bin (version 4.2.0.11-0ubuntu0.12.04.1) is present and installed.
dpkg: error processing /home/john/Downloads/skype-ubuntu-precise_4.2.0.11-1_i386.deb (--install):
 conflicting packages - not installing skype


  

Anyone know what to do? Keep it simple please ;)

---

### Post by Hekabe on 2013-06-02
Try uninstalling the skype package first. Use ```
sudo apt-get remove --purge skype
``` and then try installing from the .deb again.

---

