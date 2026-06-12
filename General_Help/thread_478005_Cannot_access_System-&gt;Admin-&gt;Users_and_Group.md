---
title: "Cannot access System-&gt;Admin-&gt;Users and Groups, Network or Services"
date: 2007-06-18
forum: General Help
---

### Post by pak33m on 2007-06-18
I recently upgraded to Feisty from Edy without any errors.  The only thing that I have done since is install network-manager-vpnc and updated when there was a kernel update (I think that is what it was).


When I try to access Usrs and Groups, Services and Network I am prompted to enter my password but then I get 
```
The configuration could not be loaded You are not allowed to access the system configuration 
```

I have selected a different kernel but I get the same problems.

I have checked to make sure that I am in /etc/groups as Admin and I am.

I have tried to access users-admin in the root terminal and i get ```
 (users-admin:6345): gtk WARNING **: cannot open display; 
```

I have completely removed and reinstalled system-tools, data-dumper and libdata-dumper-simple-perl but that just brings me back to the same problems.

Can anybody help?

---

### Post by pak33m on 2007-06-19
bump

Anybody have any ideas?

---

### Post by Sonicgoo on 2007-06-23
when booting up go into the recovery mode

then type visudo

add yourself to the users

---

