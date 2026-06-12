---
title: "DNS Redirect based on IP of requestor"
date: 2016-11-27
forum: General Help
---

### Post by Steve_Lloyd on 2016-11-27
I am currently using Dnsmasq as a private DNS server.  I have a need to redirect a domain based on the IP or MAC of the requestor.  For instance, if a certain MAC or IP requests abc.com then I want the DNS server to return one address and if someone else requests abc.com I want the DNS server to return a different address.  Is this possible?  Is there any other tools besides dsnmasql that can do this?

---

### Post by SeijiSensei on 2016-11-28
I believe it might be possible using "views" with the standard DNS server, BIND9.  [https://kb.isc.org/article/AA-00851/0/Understanding-views-in-BIND-9-by-example.html](https://kb.isc.org/article/AA-00851/0/Understanding-views-in-BIND-9-by-example.html)

I don't use views, but the examples show how the server can provide different information depending on the source-address of the query.

---

### Post by HermanAB on 2016-11-28
Or you can use iptables rules to route the DNS requests to two different DNS.

---

