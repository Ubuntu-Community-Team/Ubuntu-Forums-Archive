---
title: "Bind tinkering"
date: 2013-01-14
forum: General Help
---

### Post by ljmhk on 2013-01-14
Hey chaps!

I've got a question about bind (bind9) or perhaps its a more general DNS question. I have setup a bind server in my local office in a master/slave configuration. It handles internal domains (.lan) just fine and has a slave configuration for an external site we use for development, which also works just fine.

Now my question is, would it be possible to make modifications to that slave zone (such as an additional A record or CNAME) which is only present on that said server. The reason for this is that some of the internal machines have been configured to use that domain for hostnames for internal development. What I want to do is be able to sync the zone from the DNS provider to ensure that all the existing records are retained, but then add some additional records for use only on the internal network.

I could simply switch to master and add my amendments there, but I want to ensure there is no disparity with the live DNS (as some clients do use these records) in an automated fashion.

Could someone tell me if this is even possible with a bind configuration before I start scripting a hack into place with the master method?

Cheers guys

---

### Post by ljmhk on 2013-01-16
:cry: No ideas chaps?

---

### Post by ljmhk on 2013-03-26
The answer in the end here, was to use dnsmasq which is a much more lightweight solution. dnsmasq asks as a caching proxy server (enabled for me) and dhcp server (disabled for me). But also allows you to override the DNS records with the machine's hosts file, in effect creating a network dns server which not only caches but provides a convenient way to distribute private urls for development etc without using public A records.

---

