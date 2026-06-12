---
title: "Problems with apt-proxy"
date: 2006-11-25
forum: General Help
---

### Post by moufranica on 2006-11-25
Dear Gurus,
I installed and successfully configured apt-proxy on Edgy. But when I try to update from my clients, the apt-get utility seems to be using http_proxy to get the updates. Since my apt-proxy is on a local machine, the apt-get client is not supposed to use http_proxy. I tried to put the IP address of apt-proxy in the ignore_hosts list, but that doesn't seem to work as apt-get does not honor that!. It still keeps going through my main proxy. So how do I make apt-get behave well?

---

