---
title: "VirtualBox problems after last kernel upgrade"
date: 2008-06-07
forum: General Help
---

### Post by Samu on 2008-06-07
Hi,

I write this post because I run into a problem with the last kernel upgrade 2.6.18 regarding virtualbox. It was saying:

/etc/init.d/vboxdrv: 311: /opt/VirtualBox-1.4.0/src/build_in_tmp: not found

I could not find any decent solution online, but after looking at the script I found an easy workaround. I write it here just in case someone has the same problem. You just need to delete a file, the old vbox.cfg, or comment a line within it. One solution:

sudo mv /etc/vbox/vbox.cfg /etc/vbox/vbox.cfg_

I hope it helps someone out there,
Samu

---

