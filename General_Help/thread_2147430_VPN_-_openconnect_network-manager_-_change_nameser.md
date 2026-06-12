---
title: "VPN - openconnect network-manager - change nameserver search order"
date: 2013-05-21
forum: General Help
---

### Post by jeebustrain on 2013-05-21
So after using a shell script for the last 4 years to connect to my company's Cisco SSL VPN, I finally realized last night that somewhere along the way, the network-manager integration for OpenConnect made it really easy to connect. The one problem I seem to have though is the search order for the name servers. I can resolve internal company resources (mostly windows servers) just fine using our internal only company.org domain. Most of our company web applications, however use company.com as their domain suffix. Some of these are internal only and some resolve over the public internet. What I'd like to be able to do is change the default search order of the name servers so that it uses my company's DNS servers first and everything else second. The Cisco Anyconnect client (on windows) does this automagically. 

I've gone into the vpn connection and added company.org and company.com to the Additional Search Domains and it didn't seem to make a difference. I also made sure I dropped in a pair of internal DNS server IP addresses in the field above. The weird thing is that running nm-tool on on the terminal doesn't show any of my vpn connection information, other than that it's actually connected (no IP addr, gateway, DNS, etc...). Although this may be by design

---

### Post by jeebustrain on 2013-05-22
any ideas? I can't seem to find much documentation on the implementation of this

---

