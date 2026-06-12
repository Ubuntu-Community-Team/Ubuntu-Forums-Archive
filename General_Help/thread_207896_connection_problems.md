---
title: "connection problems"
date: 2006-07-02
forum: General Help
---

### Post by JoeeT on 2006-07-02
I am unable to connect using some applications which require internet access.

- GAIM - When I try to connect to the servers for MSN and AIM the application stays on the "connecting" status.
However, if I ping the AIM host: login.oscar.aol.com and THEN try connecting, it works. If I try this with MSN however, no packets are recieved.
If I switch to 'use HTTP method' using MSN, the aplpication stays on the "handshaking" status when connecting.

- Evolution - Pretty much the same as above, though the trick with pinging only worked just once. I am unable to connect to incoming mail servers.

- Synaptic and Apt-get - "Apt-get install" works up to the following point:

[i]joee@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
99% [Connecting to us.archive.ubuntu.com (1.0.0.0)]
[/i]

Then just freezes at that point until I give up and hit Ctrl+C to quit. Still, if I run apt-get install atferwards everything runs fine.

However, I cannot seem to download anything using Synaptic. Synaptic claims to be downloading file(s) but just stays that way until I cancel and quit.

--------------------------------------

Mozilla Firefox works with no trouble.

Most of the problems appear to be of a similar nature, so I guess it something to do with my network settings.

I connect to the internet through a router using DHCP.
For the past 10 weeks I have been connecting through my university network via a proxy and it all worked completely fine when I set the relevant proxy settings there, and when I returned home I switched to "direct internet connection" in System -> Preferences -> Network Proxy since I was no longer running on the university network. This is when the problem begun, though it occurred before I spent those 10 weeks at university. Though I think Evolution and possibly Synaptic worked before then. I'm not sure.

Can anybody please shed any light on my situation? It would be very much appreciated.

---

### Post by stonefeet on 2006-07-03
wow that is really strange, sorry i can't help you on specifics but i couldn't get gaim to connect at all until i pinged login.oscar.aol.com then gaim worked just fine

---

