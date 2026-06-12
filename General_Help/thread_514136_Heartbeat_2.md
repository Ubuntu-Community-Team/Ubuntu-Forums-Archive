---
title: "Heartbeat 2"
date: 2007-07-31
forum: General Help
---

### Post by timpickup on 2007-07-31
Hi all,

I have installed heartbeat 2 on 3 Ubuntu 7.04 machined all connected on a LAN.

For some reason the nodes keep loosing each other shortly after connecting and then refinding each other resulting in "split brain" apparently !

The consequences are.. strange.  IP addresses get assigned to more than one node at once and everything basically goes to hell.

Anyone got any ideas or advice ?  I can post logs if you tell me exactly what you want (dont want to make the post unreadable with reams of logs if not required)

Please please help !

Thanks
Tim

---

### Post by mrowen on 2007-08-01
Start with the basics. What version of Ubuntu are you doing this on? What version of heartbeat are you using? How did you install heartbeat or from what source? Its been awhile since I setup HA but I'm planning to do it with Ubuntu myself within the next week. This info will also help anyone else who happens to see this thread.

---

### Post by timpickup on 2007-08-09
Ok,
Im running Ubuntu 7.4 Feisty.

I have installed version 2 of heartbeat via > apt-get install heartbeat-2 (note: I had to update my dources i believe to do this).

I have got somewhere with my configuration but its still not right at all.

I have 3 nodes in my cluster.

I could really use a decent book or how to which covers greater than 2 node setups for heartbeat :/

anyone know any ?

---

