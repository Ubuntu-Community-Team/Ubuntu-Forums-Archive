---
title: "Problem with Ident"
date: 2007-09-04
forum: General Help
---

### Post by OterLabb on 2007-09-04
Running Ubuntu 7.04
I have tryed both "pidentd" and "oidentd", but no luck.
I have off course opened port 113 on the router, and it should be open on the box too, but I always get connection refused when I try to scan the port from a computer outside of the local network.
When I scan from a local computer the port is open.
"nmap -p 113 localhost" on the ubuntu box gives "113/tcp open auth"

But when I scan from a webpage (canyouseeme.org or pcflank.com) its closed

When I connect the eggdrop, the server always replies "No Ident response"
The router is a D-link DI-624
Anyone have a clue what is wrong?

---

### Post by vrangforestillinger on 2007-10-03
A D-Link DI-624 you say? I had big problems with ident when I tried it througt my DI-714P+. It was the last drop for my D-Link. I've also experienced problems with WiFi connections getting lost after a few minutes.

I opened the port on the computer, and set up the router so it would forward requests on port 113 to my computer. What happened was, whenever a server issued an IDENT-query, my connection was lost. My router reconnected and got a new IP, but the IDENT never got trought. It was really strange.

I was already fed up with the router, which I recently only used as an external firewall anyway. So I desided to instead set up my iptables properly with Firestarter and connect directly to the net with my Ubuntu-box. Way much easier than setting up all those virtual server entries (ssh, dcc etc).

After throwing the router away, the connection losses where gone. But the IRC-server still reported that there was some error with the ident-request/response. Instead of fiddling further with pident I just tried oidentd, and it worked out nice.

---

