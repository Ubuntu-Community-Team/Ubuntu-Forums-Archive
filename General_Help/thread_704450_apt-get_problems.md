---
title: "apt-get problems"
date: 2008-02-22
forum: General Help
---

### Post by ade234uk on 2008-02-22
About one week ago I decided to install citadel. It halted half through the installation with a permission denied message.

This has put a block on anything else I want to install via apt-get and everytime I do citadel rears its ugly head again.

I just tried to install ssh, and citadel popped up. I need to get rid of citadel permanently. How do I do this so it does not keep appearing, so I can use apt-get again.

Here is a copy from my terminal.

----------------------------------------------------------------------------

Setting up ssh (1:4.6p1-5ubuntu0.1) ...

Setting up citadel-server (7.32-31) ...
applying your settings.
..........kill: 171: No such process

..........kill: 171: No such process

/var/lib/dpkg/info/citadel-server.postinst: 78: /usr/lib/citadel-server/migrate_aliases.sh: Permission denied

---

### Post by banewman on 2008-02-22
Was citadel installed from source?

---

### Post by ade234uk on 2008-02-22
Citadel was not installed from source. I used apt-get

---

### Post by kaens on 2008-02-22
Try apt-get --fix-broken

---

### Post by lifewithryan on 2008-02-22
or apt-get remove citadel-server ??

---

