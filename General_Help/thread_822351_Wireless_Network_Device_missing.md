---
title: "Wireless Network Device missing?"
date: 2008-06-08
forum: General Help
---

### Post by Naatan on 2008-06-08
Hi,

I have an HP Pavilion dv6710ed with wifi, but in Ubuntu there is only a wired network card, though the restricted drivers manager does have the wireless card enabled.

I have tried installing the windows drivers with ndiswrapper, this worked flawlessly and it says it's installed, but when I run "ifconfig" there's only eth01 and lo, no wireless card.

Does anyone know what might cause this?

---

### Post by Kinnza on 2008-06-08
first i suggest you put this post in network & wireless cause im guessing ppl that really understand are looking there
i got help there very very fast on wireless questions

second, 
lets see your output for this command:
```

sudo lshw -C network

```

---

