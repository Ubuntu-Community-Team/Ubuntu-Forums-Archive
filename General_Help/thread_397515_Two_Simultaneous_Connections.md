---
title: "Two Simultaneous Connections?"
date: 2007-03-30
forum: General Help
---

### Post by CocoAUS on 2007-03-30
Is it at all possible to use two internet connections at the same time?  For instance, if I wanted to use my wired connection simply for serving files, and my wireless connection for normal internet usage, would this be possible?  Both my wired and wireless connections are configured and I can switch between them just fine.

---

### Post by kidders on 2007-03-31
Hi there,

What you're describing is possible ... in fact, it's almost trivial, in that a server will only bind itself to network interfaces you tell it to bind to.

So, if you have two network interfaces (eg eth0 and eth1), and your system is configured to "prefer" to use eth1, any locally initiated network connection would use that interface, if possible. If you then explicitly configure Apache & Samba, for example, to listen on eth0, those services would only be available over that interface.

---

### Post by tobodestroyer on 2008-06-10
How exactly do I do this? I'm new to Linux...

I'm desperate to get two network cards simultaneoulsy.

---

