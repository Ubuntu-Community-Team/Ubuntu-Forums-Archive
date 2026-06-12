---
title: "How to block internet"
date: 2006-11-13
forum: General Help
---

### Post by gregski on 2006-11-13
Hi all,
I'm a Linux nub and need help with setting up the following for Ubuntu v6.10 desktop:
In a business environment I would like to block all internet surfing but allow full access to our intranet.  Synaptic should also not be blocked.  That will autorun (I've figured out the autorun).
Would locking down dns do this?  Perhaps using dnsmasq?  But then does Synaptic need dns?
I would like to configure the box itself and not use an external device such as a proxy server, etc.
Any help much appreciated.
Thanks!

---

### Post by adwait on 2006-11-13
WEll blocking DNS would work, but if the dedicated users can get the IP address of the site they want to visit from home and surf away...but that might deter the casual surfer. Anyway, Synaptic does require DNS but you can circumwent that replacing the URLS in /etc/apt/sources.list with their correspoding IP addresses. Alternatively, you can add those URLs to your /etc/hosts file.

Another, more sophisticated option would be to use iptables or any other software firewalls available in Synaptic.

---

### Post by mcduck on 2006-11-13
I think the easiest way would be installing Firestarter and using that to block all IP addresses, and then whitelist the intranet.

---

### Post by gregski on 2006-11-13
Thanks for the reply.
I've done the same in windows and didn't know if there was a similar hack for ubuntu.
I've edited the hosts file to include my intranet and the ubuntu update manager.  Also set the dns server to 127.0.0.1.

---

### Post by gregski on 2006-11-13
Thanks for the reply.
I'll give that a try too!

---

### Post by krismatth3 on 2006-11-13
Uhm, how about just plain not hooking the network up to the internet? Or hire a network admin. 

Or hire people that you trust.

---

### Post by gregski on 2006-11-13
I'm a network admin myself, making my first serious foray into linux for use on our windows network.  For the first (simple) project I need a few boxes to allow users to view our intranet.  I don't want any internet surfing.  The other function it must do is auto-update the OS (from the internet).
I'm setting up firestarter and it is doing the job.

---

### Post by krismatth3 on 2006-11-13
My point is that such a thing is much better accomplished at the router level rather than on an individual box. Try as you might, it is much harder to secure machines that people have physical access to, as compared to a router locked in a closet - which has the additional benefit of no one having an account on it, and not running any client software.

---

