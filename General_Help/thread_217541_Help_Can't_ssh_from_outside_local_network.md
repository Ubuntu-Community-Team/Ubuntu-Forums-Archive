---
title: "Help: Can't ssh from outside local network"
date: 2006-07-17
forum: General Help
---

### Post by allo2u on 2006-07-17
I have installed ssh and forwarded port 22 to my box, but when I try to login using putty from my other pc, the connection is timed out. When I type in the local ip adress of the box I want to login, it works flawlessly. 
Is there something I forgot to do? Is it because I can't do this from any computer inside the local network?
I also tried the standard ubuntu remote desktop, which uses port 5900. Same problem; locally it works, but nothing when I use my external ip.

Thanks in advance for any help ;)

---

### Post by reacocard on 2006-07-17
i've had a similar problem. I had to uncheck "filter internet NAT redirection" in my router's config before it would work.

---

### Post by allo2u on 2006-07-17
Thanks reacocard, that worked, problem solved. Both ssh and remote vnc work now :-)

---

