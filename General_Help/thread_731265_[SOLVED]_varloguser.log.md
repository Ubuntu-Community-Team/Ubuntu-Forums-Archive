---
title: "[SOLVED] /var/log/user.log"
date: 2008-03-21
forum: General Help
---

### Post by Bruce M. on 2008-03-21
I'm trying to find a log file created when I shut down, I'm always getting an error regarding Network Manager but can't find the file.

This is my: /var/log/user.log - obviously not shutdown but very confusing

```

Mar 21 18:50:26 bruloo dhcdbd: Started up.
Mar 21 18:50:28 bruloo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar 21 18:50:34 bruloo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Mar 21 18:50:34 bruloo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar 21 18:50:34 bruloo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

```

What's this /com/redhat/dhcp/eth0  ?

redhat on Ubuntu?

---

### Post by Bruce M. on 2008-03-29
bump

Never thought I'd do that.  :(

---

### Post by pashashome on 2008-03-29
Howdy,
Take a look at this link...seems to be a known bug. Sorry not any more of a help.

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360]("https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360")

---

### Post by Bruce M. on 2008-03-29
> **pashashome said:**
> Howdy,
Take a look at this link...seems to be a known bug. Sorry not any more of a help.

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360]("https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360")

Ahhhhhh a know **bug** ... er ... "*undocumented feature*", guess I can accept that.  :)

Thanks for pointing it out to me, pashashome.
Bruce

---

