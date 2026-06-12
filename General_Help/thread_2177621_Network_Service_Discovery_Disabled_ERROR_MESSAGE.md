---
title: "Network Service Discovery Disabled ERROR MESSAGE"
date: 2013-09-29
forum: General Help
---

### Post by suomalainen on 2013-09-29
I got the following message:

Netword service discovery disabled

Your current network has a .local domain, which ubuntu recommends as being incompatible with the Avah network service discovery. The service is holding you up.

Thanks

---

### Post by sandyd on 2013-09-29
> **suomalainen said:**
> I got the following message:

Netword service discovery disabled

Your current network has a .local domain, which ubuntu recommends as being incompatible with the Avah network service discovery. The service is holding you up.

Thanks
[http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me](http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me)
will provide a better answer than i can :D

---

### Post by suomalainen on 2013-09-29
Thank you very much sandyd that took care of the issue!!!!
Suomalainen

---

### Post by Morbius1 on 2013-09-29
The fix is good the explanation is not:
> This notification is informing you that mDNS (Avahi) has been  disabled. It's only used for a small number of applications that only  work on the local network, it won't adversely affect your internet  connection or DNS.  The most well known use for mDNS is sharing music with Rhythmbox (or  iTunes) over your LAN. It's an Apple technology, but it's largely been  ignored in favour of uPNP or DLNA.

mDNS comes in handy in an all Linux or a Linux/OSX/iOS network since it provides lan side DNS services when none are present.

Can't ping to another machine by hostname? You can with mDNS:
```
ping hostname.local
```
Your other linux machine can't find your samba share? You can access it directly with mDNS:
```
 nautilus smb://hostname.local
```
It's the mechanism by which all apple products and now all Linux devices can find and communicate with each other and it's hardly a technology that's been ignored as the above quote suggested.

---

