---
title: "can't access apache through my ip address."
date: 2008-01-07
forum: General Help
---

### Post by vizitorq on 2008-01-07
i have no idea why but for some reason i can access my server by [http://localhost/](http://localhost/) but not through [http://myipaddress](http://myipaddress). why would this be?

---

### Post by gwbennett on 2008-01-07
Your firewall?

---

### Post by vizitorq on 2008-01-08
i don't have a firewall, i just have a wireless router, which is actually just a 4-port switch and a wireless access-point. it worked before, then i switched a few desks and machines around in the development room and when i launched it back up my apache is having these problems. does that help?

---

### Post by vizitorq on 2008-01-08
nvm i figured it out. my local ip had changed, and i just had to forward the port to the new ip.

---

