---
title: "Screen resolution can't be changed in 6.06"
date: 2007-04-18
forum: General Help
---

### Post by dbayguy on 2007-04-18
hi... gone into system , preferences , screen resolution to change from default 1280 X 1024 **to** 1024 X 768 and click on apply but it always immediately comes back up as the original default resolution in Ubuntu 6.06 1 LTS. any help will be great as this is driving me nuts Thanks :)

---

### Post by zvacet on 2007-04-19
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by dbayguy on 2007-04-22
Thanks ZVACET ... went to the link you provided and edited xorg.conf in monitor section to add Horiz Sync and Vert Refresh values for my Compaq S710 monitor as these weren't in there  originally even though my monitor was correctly recognised. Saved edited file, rebooted, but still no dice. ANY suggestions ???

---

### Post by hikaricore on 2007-04-22
Post your /etc/X11/xorg.conf file here and someone may be able to offer further assistance. :)

---

