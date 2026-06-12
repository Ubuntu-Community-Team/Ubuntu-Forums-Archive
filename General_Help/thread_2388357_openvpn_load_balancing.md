---
title: "openvpn load balancing"
date: 2018-04-01
forum: General Help
---

### Post by jj4 on 2018-04-01
I am limiting the number of connections on my openvpn server. If a server reaches the limit, I want the client to try and connect to the next server.
AT the moment I have a remote-random in the client config.
How do I get it to retry immediately upon being rejected or upon connection fail?

---

### Post by HermanAB on 2018-04-01
Can't you simply do this with Round Robin DNS?

---

### Post by jj4 on 2018-04-01
DO I need a standlone dns server for that? CLients connect to the dns and this routes it out to the separate VPN servers?
Or is a load balancer better?

---

### Post by SeijiSensei on 2018-04-01
You don't need to set up a DNS server to do round-robin DNS, but you do need control over your domain's records.  It's as easy as this:

```

vpn         IN     A   10.10.10.1
            IN     A   10.10.10.2
            IN     A   10.10.10.3
[etc.]

```

Now a request for vpn.example.com will receive a reply with a randomly selected  IP address from that list.

---

### Post by jj4 on 2018-04-01
So I can just add multiple A records in my dns entry / host?
@
www
etc

---

### Post by SeijiSensei on 2018-04-01
Well, I would limit these entries to specific host names like "www" or "vpn," though if you have an A record for the domain itself (e.g., to handle HTTP requests for example.com as well as [www.example.com](www.example.com)) you would need multiple A records there as well.

---

