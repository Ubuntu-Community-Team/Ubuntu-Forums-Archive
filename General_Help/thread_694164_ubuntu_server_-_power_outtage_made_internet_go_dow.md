---
title: "ubuntu server - power outtage made internet go down for server, can't fix it."
date: 2008-02-11
forum: General Help
---

### Post by Rafiki123 on 2008-02-11
Recently the power went out at my house and since then my server had not been able to connect to the internet. I've looked on the internet for ways to fix it and could not find anything that helped me. If anyone can help me I would be extremely happy :)

not sure if this helps:
netstat -rn
Dest.                     gate                    genmask              flags      MSS window     irtt         iface
192.168.1.0          0.0.0.0               255.255.255.0     u             0 0                   0          eth0
0.0.0.0                  192.168.1.254   0.0.0.0                 UG          0 0                    0         eth0

I also can't ping anything. it says unknown host or receive no packets. i ran the cd at boot and tried to rescue a broken system. it said network auto configuration failed. "your network is prob not using DCHP protocol. Alternatively, the DCHP server may be slow or some network hardware is not working prop."

Thanks

---

