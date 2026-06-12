---
title: "Preserving /etc/resolv.conf"
date: 2021-02-14
forum: General Help
---

### Post by rsteinmetz70112 on 2021-02-14
I'm trying to set up a  Samba-AD-DC and I've almost got it working. 
In order for it to work I need /etc/resolv.conf to point to the DNS server in samba. 
I can do that by editing /etc/resolv.conf, 
However every time I reboot the file gets overwritten.
I have stopped and masked systemd-resolved.service.
But it still get over written, 
I seem to recall the file that gets copied resides somewhere else. I could edit that.

---

### Post by HermanAB on 2021-02-15
You need to preset the data you want in dhclient.conf - for example with:
prepend domain-name-servers 8.8.8.8;

---

### Post by rsteinmetz70112 on 2021-02-15
OK I decided to:
```
chattrib +1 /etc/resolc.conf
```

---

### Post by ActionParsnip on 2021-02-15
Or add the ones you want to use in /etc/resolvconf/resolv .conf.d/head  using the usual "nameserver x.y.a.b" line. Hacky but works

---

### Post by rsteinmetz70112 on 2021-02-15
Yeah, I'm trying to get a SAMBA AD DC running. I am not really happy with any of the hacks. I'm leaning toward the anti-systemd  camp.

---

