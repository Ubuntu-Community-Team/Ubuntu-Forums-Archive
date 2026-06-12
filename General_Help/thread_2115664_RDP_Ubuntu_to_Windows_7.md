---
title: "RDP Ubuntu to Windows 7"
date: 2013-02-13
forum: General Help
---

### Post by nabz0r on 2013-02-13
Hi guys,

I have a problem which drives me crazy.. I've been looking around, googling but still couldn't find a solution to my problem so I thought someone might be able to help me here..

Through OpenVPN my RDP doesn't work and I get: Unable to connect to RDP server x.x.x.x.. I get this when I use remmina but when I use rdesktop in command prompt I get: ERROR: recv: Connection reset by peer 

Trying to connect from Ubuntu to my work PC with VPN.. The VPN works perfect but not the RDP. It worked like two weeks ago but since two weeks it stoped and I wasn't been able to fix the problem. Anyone had this problem before? All inputs are welcomed and appreciated!

---

### Post by dcstar on 2013-02-14
> **nabz0r said:**
> Hi guys,

I have a problem which drives me crazy.. I've been looking around, googling but still couldn't find a solution to my problem so I thought someone might be able to help me here..

Through OpenVPN my RDP doesn't work and I get: Unable to connect to RDP server x.x.x.x.. I get this when I use remmina but when I use rdesktop in command prompt I get: ERROR: recv: Connection reset by peer 

Trying to connect from Ubuntu to my work PC with VPN.. The VPN works perfect but not the RDP. It worked like two weeks ago but since two weeks it stoped and I wasn't been able to fix the problem. Anyone had this problem before? All inputs are welcomed and appreciated!

Make sure NLA (Network Level Authentication) is turned off on the Win box.

---

### Post by nabz0r on 2013-02-14
> **dcstar said:**
> Make sure NLA (Network Level Authentication) is turned off on the Win box.
It actually is turned off. Any other inputs?

---

### Post by nabz0r on 2013-02-16
> **nabz0r said:**
> It actually is turned off. Any other inputs?

Any other suggestions?

---

