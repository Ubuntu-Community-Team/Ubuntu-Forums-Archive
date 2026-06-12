---
title: "DHCP Troubles"
date: 2005-06-16
forum: General Help
---

### Post by manobes on 2005-06-16
Hi,

I travelled over the weekend, and the place I was at had wireless internet.  I managed to get it working however, now that I'm back in the office I cannot get wireless here. 

The IT people tell me that my computer is still requesting an IP address from the place I was at, which makes no sense.  I've tried both the graphical network-admin client, and messing with various things using iwconfig and dhclient3 (for example, I've tried dhclient -r).  I tried deleting the old DNS servers in resolv.conf, and every time I run dhclient it just puts them back.  Obviously information is being stored somewhere, but I cannot find out where.  I've also tried deleting the old lease file.  That didn't help.

This is probably a simple thing, but I cannot for the life of me find where this information is being stored.

---

### Post by Arthemys on 2005-06-16
Will your work network allow you to do static IP addressing temporarily to just see if it needs to be "jiggled." Sort of like a toilet seat handle, I've noticed that at times with anything relating to computers, just try jiggling the settings and it could just work.

---

### Post by Seer on 2005-06-21
There is a script in /etc/dhcp3/ called something like dclient-script (? going from memory here) that re-writes your resolve.conf every time you boot if you use dhcp.

You can comment out the part that rewrites the script - set things manually for a boot - uncomment and then go dhcp fresh next time round.

I'll try to remember to post back at home the true name and parts to comment when I can see my machine

---

