---
title: "edubuntu/ltsp"
date: 2007-01-20
forum: General Help
---

### Post by the slayer on 2007-01-20
Ive made a test setup of edubuntu and a thin client, in vmware. The edubuntu server boots fine, but the clients stops at the edubuntu splash screen.
The client get an ip and a kernal, so i just cant find out why it wont boot.

Could you help?

---

### Post by the slayer on 2007-01-21
I solved it!
I had to make the thin client and one nics in the server, use a virtual network! The problem was that my router(Which runs dhcp), gave the client wrong adresses.

---

