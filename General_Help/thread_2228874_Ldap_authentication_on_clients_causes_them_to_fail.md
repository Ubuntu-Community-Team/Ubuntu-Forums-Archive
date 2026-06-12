---
title: "Ldap authentication on clients causes them to fail to boot"
date: 2014-06-10
forum: General Help
---

### Post by vavoem2 on 2014-06-10
Hi.

I followed this tutorial on digitalocean to authenticate 5 ubuntu machines to the same ldap database.
[https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps)

It all works fine untill you reboot.
It just hangs.

When i remove all ldap references from /etc/nsswitch.conf it boots again, but that way i don't have ldap to authenticate against.


passwd:        ** ldap** compat
group:          ** ldap** compat
shadow:       ** ldap** compat


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

Does somebody have a clue

---

### Post by vavoem2 on 2014-06-10
I made a really dirty workaround
i created 2 scripts
one to copy a file without ldap references to /etc/nsswitch.conf
and made sure it runs on init 0 1 and 6
one to copy a file with ldap references to /etc/nsswitch.conf and restart nscd daemon
and made sure it runs on init 2 3 4 and 5
I know, it aint pretty but it does the trick.
Still hope someone knows a more elegant solution though.

---

