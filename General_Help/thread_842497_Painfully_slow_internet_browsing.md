---
title: "Painfully slow internet browsing"
date: 2008-06-27
forum: General Help
---

### Post by Sprax on 2008-06-27
So I switched on my laptop today and for some reason Im almost unable to browse the internet because it is too slow. I get timeouts etc and once I managed to login to gmail I couldnt open any messages etc... 

Its not the network because the other computers work just fine. Ideas? Im clueless.

I use firefox btw.

---

### Post by phidia on 2008-06-27
Have you changed anything recently? Was the internet ok before?
Typing iwconfig in a terminal will show you some network parameters.

---

### Post by Vivaldi Gloria on 2008-06-27
Try following in firefox. Type

```
about:config
```

in the adress bar. Find

```
network.dns.disableIPv6
```

Then double click it so the value becomes true. Restart ff.

---

