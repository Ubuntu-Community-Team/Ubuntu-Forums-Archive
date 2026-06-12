---
title: "Mail server fully qualified domain name"
date: 2015-02-25
forum: General Help
---

### Post by SchnappiJedi on 2015-02-25
Hi,

Is it a bad practice to run a mail server with a fully qualified domain name such as .lan, .local, ect.?

---

### Post by lisati on 2015-02-25
Choosing a suitable name for your server is probably a good idea, it can help with troubleshooting if your server needs to interact with other servers. 

One thing to keep in mind is that if your server is likely to connect to someone else's server, you should choose a name that is similar to your email system's public identity (i.e. domain name). Avoid having your server introducing itself as "local" to someone else's server when it isn't, as this can trigger spam filters.

---

### Post by SchnappiJedi on 2015-02-25
On an active directory based network changing the domain is next to impossible (assigning an IP outside of a NAT isn't an option as the block of IP's is used up).

Have been able to edit the postfix config file which has resulted in the mail header differing from the actual fully qualified domain name (server.domain.lan) of the server

Still though when sending a message the following part of the email header still contains the .lan fully qualified domain name (see below). Is this setup acceptable in the opinion of others here?

X-Virus-Scanned: Debian amavisd-new at hostname.domain.lan
Received: from hostname.domain.com ([127.0.0.1])
    by localhost (hostname.domain.lan [127.0.0.1]) (amavisd-new, port 10024)

---

### Post by lisati on 2015-02-25
Aaah, a lightbulb goes on for me... sometimes the needs of keeping things working nicely on a LAN are different to the needs of a WAN. :D

---

### Post by SchnappiJedi on 2015-02-26
If one changes a domain name on a LAN will this update automatically on a Ubtuntu server (after a restart) or is manually editing needed in most cases?

---

