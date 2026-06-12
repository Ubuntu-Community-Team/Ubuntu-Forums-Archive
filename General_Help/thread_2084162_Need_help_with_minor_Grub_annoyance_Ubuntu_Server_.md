---
title: "Need help with minor Grub annoyance Ubuntu Server 12.04"
date: 2012-11-14
forum: General Help
---

### Post by itpro007ca on 2012-11-14
Ubuntu Server 12.04 -only OS

Minor Annoyance:

(Emachines 180H 1366 x 768 ):

Upon bootup "input not supported",then the usual text,then Ubuntu Desktop.

I edited this back a few years agao,when I using Ubuntu Desktop,but I've forgotten how.

Can somebody refresh my memory?

Thanks,
Richard

---

### Post by windscape on 2012-11-14
Hi,

According to the link here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1044596](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1044596)
it is a regression in grub2. It can be fixed by uncommenting the GFXMODE line in /etc/default/grub, then sudo update-grub.

---

