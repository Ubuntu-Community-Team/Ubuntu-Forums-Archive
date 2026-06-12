---
title: "How do I use wireless router's DNS"
date: 2014-04-23
forum: General Help
---

### Post by ldpmz3xefhpmv2 on 2014-04-23
I have setup OpenDNS content filtering in my wireless router and all my Windows computers play nicely by getting the DNS info only from the router. but my Lubuntu computer somehow gets the DNS directly from my ISP or something else.

How do I make it use only my router's DNS?

I tried adding my router's IP under DNS Server to my router IP in IPv4 and IPv6 tabs of Network Connections Manager, and it seemed to work for a little while but again it went back to whatever non-OpenDNS setting that it had.

---

### Post by jamesisin on 2014-04-23
Can you make a screen shot of your network settings?

---

### Post by ldpmz3xefhpmv2 on 2014-04-26
First, adding Additional DNS Servers in Network Connections had no effect, or did for a very short while. [ATTACH=CONFIG]252532[/ATTACH]

Then I tried adding DNS Servers in the other Network Settings which did the trick. [ATTACH=CONFIG]252533[/ATTACH]


 
It does revert back to **127.0.0.1** after reboot but OpenDNS content filtering still seems to work with my testings, so I guess it's working. 

But is there any way I can prevent it from going back to **127.0.0.1** ?

---

