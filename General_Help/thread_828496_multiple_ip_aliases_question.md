---
title: "multiple ip aliases question"
date: 2008-06-13
forum: General Help
---

### Post by sjitan on 2008-06-13
I'm aliasing multiple IP's to eth0
hence I'll have
eth0
eth0:1
eth0:2
eth0:3

How can I run either a shell script or more specifically perl script to use a certain alias interface.

thanks

---

### Post by latna on 2008-06-13
I'm not sure what you're trying to do here. Are each of the aliases on a seperate network? If so the correct interface will always be used. If they're on the same network, let's assume the network 192.168.1.0, then the kernel will use the routing tables to decide which interface to use. See the route command for more on that.

It would go something like, delete the current route:
```
route del 192.168.1.0
```

Then add the new route:
```
route add -net 192.168.1.0 netmask 255.255.255.0 dev eth0:1
```

Not sure if it works quite that way with aliases, but it should.

---

### Post by sjitan on 2008-06-13
Thank you for your reply, what I'm trying to do is connect to a website multiple times from one computer but make it look like it's coming from multiple IP addresses from the same sub net.
I'm testing my website and I don't want to have multiple computers to do so.
Is this possible.

Regards,

---

