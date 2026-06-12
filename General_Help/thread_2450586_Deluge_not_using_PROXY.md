---
title: "Deluge not using PROXY"
date: 2020-09-17
forum: General Help
---

### Post by linuxyogi on 2020-09-17
[ATTACH=CONFIG]286968[/ATTACH][ATTACH=CONFIG]286969[/ATTACH]
(Click to enlarge)

Despite the fact that I configured Deluge to use HTTP proxy my real IP is getting exposed.
What am I doing wrong ?

---

### Post by dinkidonk on 2020-09-17
If you do not want your IP to be exposed, then all of the traffic from Deluge has to be proxied and this can only be done by using a SOCKS proxy. HTTP proxies are AFAIK only used for HTTP requests which is pretty useless in this case.

---

