---
title: "Slow ssh ?because of persistent DNS lookups?"
date: 2008-04-26
forum: General Help
---

### Post by heimdal31 on 2008-04-26
Ok, I'm new to ubuntu and desktop linux, but have a number of years managing console-only Red Hat and CentOS based systems.

Short version:  Why is ubuntu doing constant reverse dns lookups when ssh-ing to an IP address or when accepting incoming ICMP echo responses?

Long version: I set up 8.0.4 using wubi.  (I've already decided to delete that and dual boot, once I can get around to making a comprehensive backup.)  I fired up a terminal window and went to ssh into one of those console-only CentOS systems that's on the local LAN segment using its private IP (192.168.x.x).  It almost immediately asked if the RSA key fingerprint was acceptable.  However, after responding that it was, I waited a few seconds for a password prompt, which struck me as rather odd.

Some playing and packet sniffing has revealed a few odd things:

My ubuntu system asks external DNS to resolve the unresolvable 192.168.x.x address.  That redirects it to an IANA.ORG server which says that it is a private address.  The system then attempts a reverse dns using mDNS lookup for the private address, and after waiting a bit finally I see the login prompt.

I also notice that if I ping an external IP by domain name (example: ping dslreports.com) then it looks it up and sends a ICMP echo request.  The ICMP echo reply comes back in and my ubuntu machine does a reverse DNS lookup on the incoming packet.  (I had tcpdump set not to look up host names, so it wasn't that causing it.)  Morever, on every incoming ICMP echo reply, my box does a reverse dns lookup on the IP address.

If I ssh to a machine that does have a valid reverse dns, then ubuntu does a reverse dns lookup, gets an answer and I get the ssh password prompt almost immediately.

I first thought there was some time of firewall that had rules based on domain.  That would explain why some packets seem to be held until reverse DNS resolution or timeout and would explain why I was seeing rDNS for incoming ICMP echo reply packets. 

Unfortunately, I can't find anything like that.  My ssh_config is the default and there is nothing in there which would cause DNS lookups that I can see--and that would not explain the lookups on the ping packets.  I've grepped through the logs to see if the resolved domains show up anywhere, but I can't find it.

Any thoughts?

Edited to add short version question at top.

---

