---
title: "How do we set-up a traffic controlled proxy server?"
date: 2008-05-04
forum: General Help
---

### Post by descentspb on 2008-05-04
I have already setup squid and authorization in Ubuntu server for the users. Now I need to limit the amount of input (and maybe output) internet traffic for the users. Is there a way to do it?

---

### Post by Monicker on 2008-05-04
Squid has a bandwidth limiting feature, called delay pools.  Iptables also has a rate limiting module.

You might also want to read this:

[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html")

---

### Post by descentspb on 2008-05-04
thanks, i'll try that out.

---

