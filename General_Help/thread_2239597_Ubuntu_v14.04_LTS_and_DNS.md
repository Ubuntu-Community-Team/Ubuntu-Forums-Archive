---
title: "Ubuntu v14.04 LTS and DNS"
date: 2014-08-14
forum: General Help
---

### Post by stephane5 on 2014-08-14
Hi !

Since the introduction in Ubuntu 12 of a new way to handle DNS with the resolv.conf file

[https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

I need to clarify something

Inside this article

*As for dealing with DNS failures, dnsmasq often sends the DNS queries to more than one DNS servers (if you received multiple when establishing your connection) and will detect bogus/dead ones and simply ignore them until they start returning sensible information again. This is to compare against the libc’s way of doing DNS resolving where the state of the DNS servers can’t be saved (as it’s just a library) and so every single application has to go through the same, trying the first DNS, waiting for it to timeout, using the next one.*

In our setup we have a dns server who work very well with all Mac and PC inside our company but not with the new Ubuntu 14

Our router send by DHCP 3 dns addresses

[i]dns1: internal dns (running by Mac OS X Server 10.9 server 3.12)
dns2: external dns from ISP 
dns3 external dns from ISP[/i]

We had a service running on one internal server with a dns entry in our dns server

All workstation work very well except the Ubuntu Station. The machine have a intermittent problem with the DNS

After some troubleshooting we have found Ubuntu don't respect priority in the way dns order are defined

Sometime It's looking first the dns1 (like it should be) and some other time he look at dns2 or dns3 instead of dns1 (Our other stations never fail to get the DNS correctly from the DNS Server)

The IP address from the outside are not the same than the IP from our internal network (Normal)

We did a setup like explained in the link above with the resolv.conf and put nameserver with our internal dns server ip and now its working all the time correctly because it resolve the right dns name and ip form our internal dns server

My question ?

Is it a Bug in the DNS of Ubuntu ? Or this behaviour its normal (if yes could you explain me)

The way we insert a dns entry in the resolv.conf is it the right  way to force to check a certain dns first ?

Do you have any suggestion for my situation ?

Thanks in advance

---

### Post by coffeecat on 2014-08-14
Not a Forum Feedback & Help question.

*Thread moved to **General Help**.*

---

