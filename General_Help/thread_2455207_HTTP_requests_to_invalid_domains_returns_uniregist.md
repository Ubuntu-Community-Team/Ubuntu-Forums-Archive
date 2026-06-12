---
title: "HTTP requests to invalid domains returns uniregistry landing page"
date: 2020-12-14
forum: General Help
---

### Post by duckax on 2020-12-14
I am using Ubuntu 18.04. When making a HTTP request to invalid domains, I get redirected to uniregistry landing page.

More specifically, when trying to load axdv-invalid-domain.com, I get redirected to uniregistry.com/buy-domains/axdv-invalid-domain.com?src=uniregistry-lander

**This affects all HTTP clients.** Even when I use the curl command line, a HTML page is returned.

**This does not affect DNS lookups**. Using the host command, I get "Host axdv-invalid-domain.com not found: 3(NXDOMAIN)"

My computer does not seem to have any VPN or proxy configured.

How is this possible? Feels like my desktop is infected with malware. Please help!

---

### Post by TheFu on 2020-12-15
I'd guess it is your ISP trapping dns, but not really sufficient facts to know.

---

