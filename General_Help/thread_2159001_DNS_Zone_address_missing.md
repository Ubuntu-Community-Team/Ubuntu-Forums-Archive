---
title: "DNS Zone address missing"
date: 2013-07-01
forum: General Help
---

### Post by jasjotbains on 2013-07-01
Hi. I have a VPS at Godaddy and from the past 3 days, one of my sites is down. On furthur inspection, i found that there is some nameserver issue. I tried editing my DNS zone today but got this error:

***Modifying Zone jasjotbains.com***

*[COLOR=#333333][FONT=Lucida Sans Unicode]zone jasjotbains.com/IN: NS 'ns1.jasjotbains.com' has no address records (A or AAAA) zone jasjotbains.com/IN: NS 'ns2.jasjotbains.com' has no address records (A or AAAA) zone jasjotbains.com/IN: not loaded due to errors.[/FONT][/COLOR]*
[I]Bind reloading on ip-182-50-141-215 using rndc zone: [jasjotbains.com]Bind reloading on ip-182-50-141-215 using rndc: WARNING: key file (/etc/rndc.key) exists, but using default configuration file (/etc/rndc.conf)server reload successful
[/I]

I tried comparing it with an OK DNS record but with no results. Any help will be appreciated :)

---

### Post by newbie-user on 2013-07-02
Looks like you haven't assigned ns1 and ns2 to proper ip addresses. "A records" match hostname to ip address. So if it's complaining that there are no A records, then you'll need to add them.

---

