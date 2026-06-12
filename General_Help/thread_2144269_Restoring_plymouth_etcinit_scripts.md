---
title: "Restoring plymouth /etc/init scripts"
date: 2013-05-11
forum: General Help
---

### Post by xzased on 2013-05-11
Hi. I did something dumb and removed all plymouth scripts under /etc/init/ and now my laptop won't boot into graphics mode. I tried reinstalling plymouth (aptitude reinstall plymouth) and reconfiguring it (dpkg-reconfigure plymouth) but that does not generate the scripts. Is there a way I can restore them?

---

### Post by Bashing-om on 2013-05-11
xzased; Hi !

I do not know for sure, might be worth a shot :
Boot up the liveCD, and in the liveCD's file manager compare the files present in the live cd /etc/init to the install's /etc/init and copy the needed  files across from the liveCD to the install ?
[INDENT=2]
just a thought

[/INDENT]

---

