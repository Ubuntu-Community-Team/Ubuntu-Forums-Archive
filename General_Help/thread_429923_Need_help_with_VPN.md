---
title: "Need help with VPN"
date: 2007-05-01
forum: General Help
---

### Post by Krystoll Meth on 2007-05-01
Trying to connect to my Ubuntu 7.04 home system from my windows XP office system. I'm behind a router at home but we're able to connect to our office computers from home and vice versa, so I want to connect to my home system from there. Need some help please

---

### Post by dcstar on 2007-05-01
> **Krystoll Meth said:**
> Trying to connect to my Ubuntu 7.04 home system from my windows XP office system. I'm behind a router at home but we're able to connect to our office computers from home and vice versa, so I want to connect to my home system from there. Need some help please

You will (most likely) need to open ports on your home router - these will depend on the software you want to use to connect remotely to your Ubuntu machine.

There may be HOWTOs with detailed instructions for your particular router, do a web search for them.

---

### Post by jlsheehan on 2007-05-01
> **Krystoll Meth said:**
> Trying to connect to my Ubuntu 7.04 home system from my windows XP office system. I'm behind a router at home but we're able to connect to our office computers from home and vice versa, so I want to connect to my home system from there. Need some help please

Hi,

I think you will need to run the pptpd server on your Ubuntu system so that the windows client has something to talk to.  Then of course you would need some services running on your network that windows can actually use....samba perhaps?

Jeff

---

