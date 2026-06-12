---
title: "Azureus port binding"
date: 2006-07-10
forum: General Help
---

### Post by g00fy on 2006-07-10
Hi,


I have a problem with azureus... It's not binding on the port it should. So in Azureus I say port 12358, and after restarting the program this shows up in a netstat:
```
tcp6       0      0 :::12358                :::*                    LISTEN
udp6       0      0 :::12358                :::*
```

As you can see it only binds to tcp6, but not to tcp (like for example the svn service:
```
tcp        0      0 0.0.0.0:3690            0.0.0.0:*               LISTEN
```)

How can I make it bind to tcp too?


Thanks!

---

