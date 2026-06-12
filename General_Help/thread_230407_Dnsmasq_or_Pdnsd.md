---
title: "Dnsmasq or Pdnsd?"
date: 2006-08-05
forum: General Help
---

### Post by dr_d on 2006-08-05
Hi folks,

I just finished reading an article about setting up a local dns server to provide caching, and ultimately make my browsing faster.

I really like the idea an cant wait to give it a try, but I'm unsure which dns server package I should use.

I've used dnsmasq before and quite like it, but is it true that dnsmasq does not provide permanent caching?

I think it's pretty important that I have permanent caching because I'm running ubuntu on a laptop and the chances that I'd visit a site twice before rebooting seem somewhat slim.

Any suggestions would be appreciated.
Cheers.

---

### Post by sciurus on 2008-05-04
It's sounds as thought you want to have the caching dns server save its cache to disk when you shut down your laptop and then read it again when you power back on. I doubt this is very valuable, the ttl for most DNS records is so low that your cache will be stale.

---

