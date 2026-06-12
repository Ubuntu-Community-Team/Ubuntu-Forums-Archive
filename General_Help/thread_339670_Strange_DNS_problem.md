---
title: "Strange DNS problem"
date: 2007-01-16
forum: General Help
---

### Post by chio on 2007-01-16
I've got a bizarre problem with DNS resolving in Edgy - bear with me, it might take a bit of explaining!

If I'm in Firefox and open a page in one tab, then before that page has finished loading open another page in another tab, something seems to get a little confused and start resolving both domains to the same IP.

For example, if I was to open [www.ubuntuforums.org](www.ubuntuforums.org) in tab 1, then [www.bbc.co.uk/news](www.bbc.co.uk/news) in tab 2 before tab 1 had finished loading, the BBC address would resolve to the Ubuntu forums one and I'd get a 404 from *this* site saying it can't find [www.ubuntuforums.org/news](www.ubuntuforums.org/news) in tab 2. Changing browser to Opera doesn't help.

It even does this if I've got the AJAX start page Netvibes open in a tab, and it happens to be updating a feed at the time I'm loading a page in another tab (the site whose feed it is "takes over" from the real site I'm trying to load in tab 2). The fault sticks until I turn the computer off and on again.

I'm connecting to the internet through a wired LAN and a BT home router, using OpenDNS for DNS. The same problem occurs when using my ISP's DNS servers. The problem doesn't occur when using the Windows installation on the same machine (dual boot) or a separate Mac machine on the same network. I'm running the very latest updates. 

Any help would be gratefully received! 

:KS

---

### Post by chio on 2007-01-27
I hate to bump this up, but does no-one have any ideas? It's becoming the one thing stopping me wanting to use Ubuntu.

---

### Post by dexter on 2007-01-27
You could try another browser first (eg Opera) to determine whether it is a Firefox issue or not.

---

### Post by koenn on 2007-01-27
> **dexter said:**
> You could try another browser first (eg Opera) to determine whether it is a Firefox issue or not.
good point.
if it's not related to firefox : do you use a web proxy of any sort ?

---

### Post by dcstar on 2007-01-27
> **chio said:**
> I've got a bizarre problem with DNS resolving in Edgy - bear with me, it might take a bit of explaining!
........
I'm connecting to the internet through a wired LAN and a BT home router, using OpenDNS for DNS. The same problem occurs when using my ISP's DNS servers. The problem doesn't occur when using the Windows installation on the same machine (dual boot) or a separate Mac machine on the same network. I'm running the very latest updates. 

Any help would be gratefully received! 

:KS

What are the IP addresses/configuration you have when using Linux compared to Windows?

I would guess it is a NAT issue with incorrect port mapping somewhere.

---

### Post by sysctl on 2007-02-05
I can fully confirm your problem (I have it), and I think it is related to Firefox. Most often the problem manifests itself when you restore the browsing session, sometimes at random.  I try to open help.ubuntu.com and it resolves to google.com(???), sometimes to BBC (default bookmark in Firefox). During the glitches, there are either no DNS lookups in Ethereal, sometimes it says "malformed packet" in DNS response. The problem disappears in a few minutes, but reappears later, and does so quite often.

And yeah, I'm NAT'ted (D-Link DSL-G604T), though with the latest firmware.

---

### Post by sysctl on 2007-02-05
OK, I **think** I have solved my problem by disabling IPv6 DNS again in Firefox.

It is a different IPv6 DNS problem from that I was having last time (not being able to resolve anything at all). I upgraded my DSL router's firmware and the first problem disappeared, so I re-enabled IPv6 DNS back only to have another problem appear.

---

### Post by chio on 2007-02-20
> **sysctl said:**
> OK, I **think** I have solved my problem by disabling IPv6 DNS again in Firefox.

It is a different IPv6 DNS problem from that I was having last time (not being able to resolve anything at all). I upgraded my DSL router's firmware and the first problem disappeared, so I re-enabled IPv6 DNS back only to have another problem appear.

Nice one - I changed the setting you suggested a few days ago and I've been running my system with no trouble whatsoever since. My ISP doesn't "do" IPv6 anyway, so there's not really a lot of point having it switched on! 

Many thanks.

:KS

---

