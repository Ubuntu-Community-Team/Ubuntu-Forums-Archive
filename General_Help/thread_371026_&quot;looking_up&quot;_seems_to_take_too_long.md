---
title: "&quot;looking up&quot; seems to take too long"
date: 2007-02-26
forum: General Help
---

### Post by Morientes on 2007-02-26
I have noticed that my firefox browser in Kubuntu 6.10 takes a little too long looking up DNS. I mean it does it for sites that I have just visited. It doesn't take VERY long time - just a bit too long I think.
If I have JUST visited a site, then two seconds later it shouldn't be looking up at the DNS again should it?
It seems like there is some sort of small problem with the DNS. In Windows my computer does not do it. I have disabled ipv6 in Firefox, but that doesn't seem to have helped.
I think the problem is also in other applications besides Firefox.

Any ideas what I might do to solve this problem?

---

### Post by Maestro23 on 2007-02-26
Have you tried to disable IPv6 system wide?

[http://ubuntuforums.org/showpost.php?p=1942241&postcount=6](http://ubuntuforums.org/showpost.php?p=1942241&postcount=6)

---

### Post by r4ik on 2007-02-26
If your router is using dhcp:

The best bet would be to put your isp's primary and backup dns server addresses in your router's setup page. That way, when /etc/resolv.conf gets overwritten upon re-lease or reboot by dhclient, your isp's dns addresses will be there. Dhclient sometimes stops detecting anything beyond the dns-forwarder in our low-cost routers - but that is a whole different story - not dhclient's fault!)

The other option is to manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

Manually editing addresses in /etc/resolv.conf when you are running dhcp in the router only lasts temporarily as dhclient will overwrite /etc/resolv.conf upon re-lease or reboot. Making resolv.conf read-only doesn't work, and using chattr to make it immutable isn't advisable.

Of course you could run static and resolv.conf will be left the way you edit it, but what fun is that?

I also disable IPV6 globally by running the following as root:
Code:
echo "blacklist ipv6" > /etc/modprobe.d/blacklist

then followup by disabling ipv6 in Firefox as well. At this point I just reboot.


Also try about:config in the adresbar and set the "pipe" maxrequest to 8

Good luck !

---

### Post by 1985mars on 2007-11-11
Thanks guys disable of ipv6 works for me

---

