---
title: "exim4, gmail  and 550-5.7.1"
date: 2015-12-11
forum: General Help
---

### Post by rsteinmetz70112 on 2015-12-11
I run two mail servers one postfix and the other exim4, both on Ubuntu.

Any email to a gmail account or a domain whose mail is hosted on a gmail server is rejected with a 550-5.7.1 error, basically requiring a ipv6 ptr record.

I have known about this problem for a while but used other workarounds. Recently we have seen more and more people hosting their email on gmail using this own domains. So I decided it was time to solve the problem permanently. Unfortunately our IP addresses are provided by our ISPs and they don't provide ipv6 ptr records.

I solved it with the postfix server by setting up a list of domains to be to ipv4 only. That works well and is easy to add more domains as I discover them

Is there a comparable method for exim4? Or some other way of overcoming the problem? I have Goggled around and the postfix answers came up pretty easily, I've found very little on exim4.

I did find this web page:

[https://github.com/Exim/exim/wiki/How-to-force-IPv4-connections-for-specific-domains-if-IPv6-is-enabled](https://github.com/Exim/exim/wiki/How-to-force-IPv4-connections-for-specific-domains-if-IPv6-is-enabled)

But I'm not sure how to implement it. I can certainly add a Router and Transport to the appropriate directory, but where should the domain list go under conf.d?

---

### Post by rsteinmetz70112 on 2015-12-17
Based on the link I listed in my first post I have come up with a potential solution:

Can anyone comment on whether shouid should work or not?

I propose adding a new files in /etc/exim4/conf.d/main

05_ipv4_force_domains

Containing:

domainlist ipv4_force_domains = \
 gmail.com : \
 googlemail.com : \
 virgin.net : \
 linkedin.com : \
 virginmedia.com


Greping router for remote_smtp

I get

100_exim4-config_domain_literal:  transport = remote_smtp
150_exim4-config_hubbed_hosts:  transport = remote_smtp
200_exim4-config_primary:  transport = remote_smtp
200_exim4-config_primary:  transport = remote_smtp
200_exim4-config_primary:  transport = remote_smtp_smarthost
500_exim4-config_hubuser:  transport = remote_smtp_smarthost


So I propose adding a new file to /etc/exim4/conf.d/router called

050_exim4_config_ipv4_only.

Containing

ipv4_only:
 driver = dnslookup
 domains = +ipv4_force_domains
 transport = ipv4_smtp
 ignore_target_hosts = <; 0::0/0|

Finally adding a file in /etc/exim4/conf.d/transports

50_exim4_config_ipv4_only_transport:

I'm a little puzzled by the one in the example.

ipv4_smtp:
 driver = smtp
 dkim domain = mydomain.co.uk
 dkim_selector = x
 dkim_private_key = /usr/exim/dkim.private.key
 dkim_canon = relaxed
 interface = <my.v4.ip.address>|

Why can't I simply use the existing smtp remote_smtp transport with
the some relatively simple edits? This example contains a directive
that limits it to using ipv4 by  specifying the interface using an
ipv4 address. Seems like somewhere should be a directive like
disable_ipv6 = true or dns_ipv4_lookup = *

I also wonder if these dkim statements conflict with the rest of the
basic debian configuration.

---

