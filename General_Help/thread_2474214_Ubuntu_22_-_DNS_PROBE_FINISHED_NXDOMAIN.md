---
title: "Ubuntu 22 - DNS_PROBE_FINISHED_NXDOMAIN"
date: 2022-04-24
forum: General Help
---

### Post by eletron-dalton on 2022-04-24
Hi!

I've recently tried to update from Ubuntu 20 to V22, but I am getting an error when trying to access through FortiVPN Client local pages at my company. We have some internal webpages for time registration and even the internal gitlab account and I can't access them. I get an error of [COLOR=#202124][FONT=arial]DNS_PROBE_FINISHED_NXDOMAIN; It only happens at those local webpages, the rest is working fine.
Can someone help me solve this issue? I was really into upgrading all my 3 machines to V22, but I can't if this error persists; Also, in V20 of ubuntu this error does not happen, although the first time I visit one of those pages I get an certificate error and an option to proceed;

Thank you in advance, and best regards![/FONT][/COLOR]

---

### Post by challdns on 2022-04-24
This will not work without dns forwarding for specific domains across the vpn tunnel.

Im guessing it was cached in your machine before from being on it locally, and that was lost when you upgraded.

You can add these sites, if they are static, to your hosts file. That way your computer will resolve the names locally. 


Also, you can turn off split tunneling and force all your traffic across the vpn tunnel and it should resolve the issue as well.


If you get the IP address and go to the IP address it will work.

---

### Post by eletron-dalton on 2022-04-24
Thank you Challdns for helping, i'll try those solutions!

---

