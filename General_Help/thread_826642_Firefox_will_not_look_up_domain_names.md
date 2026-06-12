---
title: "Firefox will not look up domain names"
date: 2008-06-12
forum: General Help
---

### Post by angrymob on 2008-06-12
For the past few days, I have not been able to use firefox to browse the internet via fully-qualified domain names. That is, if I enter "http://www.google.com/" in the URL bar, firefox will hang indefinitely, telling me it is "Looking up www.google.com". The symptoms are as follows:

DNS works fine everywhere else. I can ping hosts, use whois, ssh, and can browse via domains with other browsers such as konqueror. The bug persists regardless of what wireless AP/router I am connected to (I've tried at least four different points so far). Firefox is definitely capable of opening pages - if I enter the IP address, it loads the page fine, though following URLs thereafter is impossible because it fails to resolve names again. The issue also persists regardless of what version of firefox I use - firefox 2.0, 3.0b5, 3.0rc1 through rc3 all fail to resolve names in the same way. Changing nameservers does not help. Deleting my firefox profile does not help. Disabling ipv6 does not help. I have no proxies enabled. Wireshark reveals that firefox is not even attempting to send out DNS query packets, so I'm not sure what it's doing at all.

---

### Post by komputes on 2008-06-12
I think I had this issue in the past.

I would guess to check your DNS Server is valid. If you have a static IP, attempt to use DHCP. Also make sure you are not using a network proxy, or a proxy in firefox.

Hope this helps.

---

### Post by angrymob on 2008-06-12
I tried all of those things before (other than the static IP thing - I was already using DHCP). I have the feeling the bug has to do with some shared library I updated, but I have no idea which one, or why.

---

