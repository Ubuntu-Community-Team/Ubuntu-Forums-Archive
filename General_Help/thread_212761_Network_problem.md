---
title: "Network problem"
date: 2006-07-10
forum: General Help
---

### Post by macoute on 2006-07-10
I installed edubuntu to a classroom. Everything works fine if I only use 1 computer at a time, but if there is more clients connected, the amount of collisions increases heavily and clients become very slow.
The server is 3.0 G Xeon w/ 2 gig ram and a gigabyte network adapter. Im not sure of the networks infrastructure, but at least the network adapters in clients are 10/100.

Where should I start? This seems to be a network problem, doesnt it? Currently ifconfig shows:
```

          collisions:210787 txqueuelen:1000
          RX bytes:181011850 (172.6 MiB)  TX bytes:1115670457 (1.0 GiB)
          Interrupt:169

```

Server only has 1 network adapter at the moment. The same adapter handles the traffic to internet and in this network. Could that be the problem? Should I add another network adapter to handle the traffic inside the network?

---

