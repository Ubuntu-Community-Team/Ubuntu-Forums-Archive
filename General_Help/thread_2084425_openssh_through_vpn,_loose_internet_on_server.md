---
title: "openssh through vpn, loose internet on server"
date: 2012-11-15
forum: General Help
---

### Post by savagetwinky on 2012-11-15
I'm having a bit of an issue logging into a ubuntu 12.10 machine. It's my work machine so I start our company vpn to be able to openssh to it. But when I use openssh through the vpn i can't access the internet any more through the server. So I can't download things to my work machine.

Also I tested this before I left work, it works fine if I'm on the same network.

Any help will be good! thanks.

edit: oops, the server doesn't have loose internet, it lost internet...

---

### Post by savagetwinky on 2012-11-15
Found out, it has nothing to do with the vpn, right before i left i changed the network from dhcp to static but for some reason static doesn't work with with the gateway. It could be gateway or it could be something funky with 12.10

---

