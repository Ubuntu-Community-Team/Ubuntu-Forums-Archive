---
title: "Port 80 closed"
date: 2014-12-11
forum: General Help
---

### Post by Bob_Mendon on 2014-12-11
I have scoured all the possible related posts about port 80 being closed when viewed externally but nothing that was suggested seems to work. I am running Server 14.04 with LAMP installed. I have tried to get to port 80 from port checkers and they all inform me that 80 is closed. I have enabled UFW and added port 80 and it doesn't work. What am I missing here? I have been using ubuntu for many years and never have I had this much trouble.

---

### Post by Impavidus on 2014-12-11
Have you checked the firewall build into your router (if you have one)?

---

### Post by Bob_Mendon on 2014-12-11
Yes. port 80 is forwarded.

---

### Post by dragonfly41 on 2014-12-11
Here is another port checker which is useful ... ShieldsUp .. [https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

[later edit]

p.s.
It could be that your ISP blocks port 80 usage.  Check their policy.

---

### Post by The Cog on 2014-12-11
Does the port show as listening when you use this command?
```
netstat -nlt
```
If not then you need to figure out why apache is not running/opening the port.

---

### Post by Bob_Mendon on 2014-12-12
It's always something simple. Although I had opened the right ports on my router, the router need to be rebooted for some reason and that fixed everything.

---

