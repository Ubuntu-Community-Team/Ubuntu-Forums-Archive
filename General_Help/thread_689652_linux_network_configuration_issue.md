---
title: "linux network configuration issue"
date: 2008-02-06
forum: General Help
---

### Post by ryjax01 on 2008-02-06
When I start up my linux box, box001 running ubuntu 7.04, its connection to the network seems appears fine.

box001 can ping all other xp/linux boxes and vice versa. However after a certain amount of time, the other xp/linux boxes can no longer see or ping box001 both via name and ip. 

Also, box001 can no longer ping or see any other xp/linux boxes via name or ip.

I am inclined to believe that box001 has a configuration issue because box001 is running a guest OS via vmware, box002 running ubuntu 7.04. While box001 cannot see or cannot be seen by any other boxes, box002 works normally.

I hope I haven't confused anyone and any help is greatly appreciated.

If I can further clarify with posting configuration data, I'd be happy to comply, but I'm just not sure which tools I to use.

This is really strange and I'm not exactly sure what happened since box001 was working fine.

---

### Post by upthelum on 2008-02-06
Set the networking for that virtual machine to "NAT", this usually works fine, does for me anyway...

---

