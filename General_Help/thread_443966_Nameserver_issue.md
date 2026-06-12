---
title: "Nameserver issue?"
date: 2007-05-14
forum: General Help
---

### Post by Howard Kaikow on 2007-05-14
I've tried running from LiveCD, version 7.04.

I installed gnome-ppp, and it successfully identified my modem on ttys1.
I was able to dial out and my ISP confirmed that I was connected.

But, Firefox cannot find any URL.
Evolution can find neither the incoming nor outgoing mail servers.
I cannot ping anyone.
I cannot ftp.

My ISP cannot ping me.

I am using a an internal Courier dial up modem.
Could Linux be trying to go thru the router, not connected to the internet, that I use for my local network?
Is there a linux firewall issue?

Here's more info.

Quote:
--> PPP negotiation detected.
--> Starting pppd at Sun May 13 19:30:09 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 12012
--> Using interface ppp0
--> local IP address [I removed address here]
--> remote IP address [I removed address here]
--> primary DNS address [I removed address here]
I can ping the local and remote IP addresses, but not the DNS address.
Are the Warnings above relevant to my problem?

Why can't I ping the primary (or secondary)  DNS?
I ca nping from Windows 2000.

Am I missing some setting?
Or did I just stumble upon a bug?

---

### Post by Howard Kaikow on 2007-05-15
Eureka!

I am posting this from Firefox in Linux LiveCD.

As I expected, the inability to see the DNS was due to a conflict 'tween PPP and the router.

Apparently, Linux goes to the router for the DNS even if you are dialing in thru a modem and not using broadband.

Windows does not have this problem, so maybe there is a Linux setting to avoid the problem?

I was able to  dial in, by unplugging the router before I booted to the LiveCD.

---

### Post by kb2wdi on 2007-05-15
The nameserver settings are in "/etc/resolv.conf" and put there by dhcp from the router.

Check your routing table; "route -n" for a default route [0.0.0.0] / 0

Drop the default route to the router with "route del -net" command.

If you installed this (not live CD), you could use a dhclient.conf file to ignore the default route and nameservers pushed from the router.

---

### Post by Howard Kaikow on 2007-05-15
> **kb2wdi said:**
> The nameserver settings are in "/etc/resolv.conf" and put there by dhcp from the router.

Check your routing table; "route -n" for a default route [0.0.0.0] / 0

Drop the default route to the router with "route del -net" command.

If you installed this (not live CD), you could use a dhclient.conf file to ignore the default route and nameservers pushed from the router.

Thanx.

It may not be a nameserver issue.

If I plug in the router and try to ping something, nothing happens.
I believe that when wired network is enabled, Linux is trying to go tru the router instead of the modem.

With the router plugged in, if I disable the wired network, then things go thru the modem.

This is not good.

What if I need to do things on the internet, and, at the same time, use files on the network.
Is not there a way to do this?

---

### Post by kb2wdi on 2007-05-15
The 2 networks CAN co-exist. The wired network is getting a default route (0.0.0.0 / 0.0.0.0) which is why traffic intended for the internet is going to it. You need to drop this default route, so only the default route from ppp is used. This required modification to files in "/etc" directory which would be lost on a Live CD, but not a real filesystem. You can make the temporary changes from a terminal window.

route -n ; to list routing table

route del -net 0.0.0.0 gw 192.168.1.0  # adjust as needed to drop the default wired route.

You should still have a route [192.168.1.0] / 255.255.255.0 which will connect to local servers in that network.

You should also get some routes added when ppp0 comes up including;

0.0.0.0  <x.x.x.x>  0.0.0.0 ppp0 # Default route to internet.via ppp0

---

### Post by Howard Kaikow on 2007-05-15
Thanx.

I'll do that when I actually install ubuntu.

---

### Post by Howard Kaikow on 2007-05-15
What about adding "replacedefaultroute" in the pppd file?

Would that get the job done?

I saw this mentioned in the SetUpDialer HowTo document.

---

