---
title: "Squid Transparent Proxy with DRBL NAT Services - UBuntu 14.04 Server"
date: 2016-03-17
forum: General Help
---

### Post by alhughes42 on 2016-03-17
I am currently using DRBL/Clonezilla as an imaging station, that also servers as a NAT server for the clients that a recently imaged. The issues I'm having is, I need to use Squid Proxy to cache some of the downloaded content from the clients so that it cuts down the download time and reduces stress on my server. 

The DRBL box is directly behind the squid proxy, then the downstream clients. So, it goes Proxy -> DRBL Server -> clients to be imaged. The DRBL server is configured for my squid proxy and it is working correctly. I can see that the traffic is running through squid and the cache directory grows with use. However, the same does not apply to the clients. 

I'm somewhat stuck here, but I do believe it has something to do with the MASQUERADE option configured when using DRBL as a NAT server.

Any help / feedback is welcome. I would love to have someone to bounce ideas off of.

---

