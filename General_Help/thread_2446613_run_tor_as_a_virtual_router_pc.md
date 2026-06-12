---
title: "run tor as a virtual router pc"
date: 2020-07-03
forum: General Help
---

### Post by touficabboud4 on 2020-07-03
hey,there is a way to run tor on ubuntu in a way that any connection from my pc pass through the tor network? like using a regular software but with tor connection

---

### Post by uninvolved on 2020-07-03
You can download the TOR browser, run it, and then configure your network connection to use a proxy. It's a SOCKS v5 proxy at 127.0.0.1 on port 9150 or 9050. You can also install and run TOR browser and then configure individual browsers to use those same proxy settings. You can configure TOR to use a different port, as well.

This link should have enough info:
[https://tor.stackexchange.com/questions/6939/configure-tor-as-proxy](https://tor.stackexchange.com/questions/6939/configure-tor-as-proxy)

---

### Post by T6&amp;sfpER35% on 2020-07-03
what have you got to hide ?:tongue:

---

### Post by ActionParsnip on 2020-07-03
Sure. You can setup squid as a proxy but I think you can setup an SSH tunnel to the Tor system and use that to proxy the traffic

---

