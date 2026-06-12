---
title: "Synaptics through Proxy"
date: 2005-05-18
forum: General Help
---

### Post by ejms07 on 2005-05-18
How can I put to work synaptics through a proxy/firewall ?  I'd setup our proxy server on synaptic's settings but doesn't work, and I have internet connection on my desktop using the same proxy.

---

### Post by blueplazma on 2005-05-18
Synaptic just uses port 80, so if you set the default proxy settings you should be ok.  What error do you get?

---

### Post by Seth on 2005-05-18
[QUOTE=ejms07]How can I put to work synaptics through a proxy/firewall ?  I'd setup our proxy server on synaptic's settings but doesn't work, and I have internet connection on my desktop using the same proxy.[/QUOTE]
 $ sudo gedit /etc/apt/apt.conf
Put in that file: **acquire::http::proxy "http://username:yourpass@proxyaddress:theport";**

---

### Post by ejms07 on 2005-05-18
The error is that cannot download repositories indexes.

I don't have an apt.conf inside /etc/apt/

---

### Post by ejms07 on 2005-05-18
I created the file with your instructions and work like a charm, Thanks Seth!

---

