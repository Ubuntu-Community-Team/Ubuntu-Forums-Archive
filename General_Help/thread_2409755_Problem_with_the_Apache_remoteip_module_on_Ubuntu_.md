---
title: "Problem with the Apache remoteip module on Ubuntu Server 18.04.1 LTS"
date: 2019-01-06
forum: General Help
---

### Post by grigutis on 2019-01-06
Hi,

I have an Ubuntu Server 18.04.1 LTS and am running Apache 2.4.29 from the standard apt repo. I'd like to put it behind a reverse proxy, but in order to get the real client IPs instead of the IP of the proxy, I'd need to use the remoteip module and the [RemoteIPProxyProtocol]("https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html#remoteipproxyprotocol") directive (AFAIK, please correct me if I'm wrong). The only problem is that while the version of Apache that I get from apt includes this module, the RemoteIPProxyProtocol and RemoteIPProxyProtocolExceptions directives are "only available in httpd 2.4.31 and newer."

So a couple of questions:
How can I get Apache &#8805; 2.4.31 on Ubuntu Server 18.04.1?
Will the version of Apache in the apt repo eventually be updated (so I should just wait a while)?
Would upgrading to Ubuntu 18.10 get me a newer version of Apache?

Any advice appreciated.

---

