---
title: "INCREASING SECURITY: /etc/hosts.deny"
date: 2006-08-13
forum: General Help
---

### Post by ProjectGod on 2006-08-13
hi gang, 

i've been reading some material concerning NFS. this requires Portmap daemon to be running. anyway since it won't hurt to explicitly deny all services from all hosts on the network or from the internet to my ubuntu client machine, i wish to add this entry into the /etc/hosts.deny file. 

i read that to do this and increase security all you have to do is insert:

**ALL:ALL**

but reading the comments in /etc/hosts.deny file... i found something about an entry looking like:
[B]
ALL: PARANOID[/B]

which would i use?

many thanks.

---

### Post by ProjectGod on 2006-08-13
no worries found the info.

[B]ALL: ALL
[/B]
is just fine.

---

