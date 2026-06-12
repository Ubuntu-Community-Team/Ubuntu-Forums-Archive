---
title: "F-Prot on Bootup"
date: 2005-05-31
forum: General Help
---

### Post by ceti on 2005-05-31
[i][b]Automatically run the Daemon Scanner at bootup:

[/b]Daemon startup files are contained in the tools/rc_scripts/ directory

cp /usr/local/f-prot/tools/rc_scripts/f-protd.rc-debian /etc/init.d/f-protd     /etc/init.d/f-protd start     And create links from the runlevel directories (f.ex. /etc/rc3.d)     to /etc/init.d/f-protd

[/i]How do I set this up? Is this a shield? Do I need this to protect my computer since I boot-up?

---

