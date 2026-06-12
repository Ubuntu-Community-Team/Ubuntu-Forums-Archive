---
title: "Remote VPN server setup."
date: 2012-12-10
forum: General Help
---

### Post by PinkFloyd102489 on 2012-12-10
I've followed several guides, which are mostly the same, on how to set up a VPN server. I've installed pptpd, setup the chap-secrets, implemented IP masquerading, forwarded port 1723, etc.

The problem I'm having is that I'm unable to connect. I've tried setting up a connection on my Android device, through Windows, and through Ubuntu. All give me an "Unable to connect".

Is there a way to see exactly what the issue is? One guide said to check the syslog but all I can see is the pptpd daemon starting up, no actual connections.

Any help is appreciated, thanks.

---

### Post by Cheesemill on 2012-12-10
I've had much more success using OpenVPN instead of pptpd.
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

Security wise it's also good not to use PPTP connections as the protocol is inherently unsecure and can be cracked without too much effort.
[http://www.h-online.com/security/news/item/Microsoft-says-don-t-use-PPTP-and-MS-CHAP-1672257.html](http://www.h-online.com/security/news/item/Microsoft-says-don-t-use-PPTP-and-MS-CHAP-1672257.html)

---

### Post by DuckHook on 2012-12-10
> **Cheesemill said:**
> Security wise it's also good not to use PPTP connections as the protocol is inherently unsecure and can be cracked without too much effort.

+1 Cheesemill

In cited article :"The [OpenVPN]("http://www.h-online.com/features/Simple-VPNs-with-OpenVPN-747368.html") open source protocol is not listed in [Microsoft's] recommendation". Of course not. That would underline the fact that a FOSS solution was infinitely superior an MS one, and had been for years. Sometimes, their self-denial is just... sad.

---

