---
title: "How to reduce virtual terminals to only one?"
date: 2007-08-25
forum: General Help
---

### Post by Marcelo Ramone on 2007-08-25
In Fedora, I just edit /etc/inittab and comment some lines to reduce virtual terminals from six to one.

But i don't know how to do it in Ubuntu 7.04

Thanks in advance,
Marcelo Ramone.-

---

### Post by K.Mandla on 2007-08-26
In 6.10 the inittab structure was changed so that virtual terminals were spawned from /etc/rc.d. If you delete the tty2, tty3, tty4, etc., files from that folder, you'll lose those on reboot.

---

