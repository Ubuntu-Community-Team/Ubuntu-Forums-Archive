---
title: "synaptics firewalls proxies and other strange things"
date: 2005-07-05
forum: General Help
---

### Post by oly on 2005-07-05
hi,
does synaptics need any specials port opened ??
i am trying to use it through a proxy and am unsure if the proxy is blocking it or a firewall is.
if synaptics works through port 80 it should work i would have thought but it does not even though i have put in the proxy info web browsing works fine though with same details.

---

### Post by bihan on 2005-07-05
[QUOTE=oly]hi,
does synaptics need any specials port opened ??
i am trying to use it through a proxy and am unsure if the proxy is blocking it or a firewall is.
if synaptics works through port 80 it should work i would have thought but it does not even though i have put in the proxy info web browsing works fine though with same details.[/QUOTE]
 hi,

synaptic needs your proxy parameters to work. Open a console, type :

export http_proxy=http://[login]:[pwd]@[yourproxy]:[proxyport]

bihan

---

