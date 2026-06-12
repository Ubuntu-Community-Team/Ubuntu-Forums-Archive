---
title: "VPN software - IPSec"
date: 2007-11-06
forum: General Help
---

### Post by RudolfMDLT on 2007-11-06
Hi there,

My Univirsety uses IPSec as their protcol for their VPN. I've had a really bad time trying to get this to work. My question is: Is it possible, in Linux, to setup an IPSec VPN connection wothout a IP-Sec ID and without a Group password, with only a username and password - thats the convention we are using. I'll even pay for software because I really need to get this working.

Secondly - is there a way that I can see whar protocols and connections are being used in windows? I've been able to setup the VPN in Windows, in under a minute :'( , using software provided by the Univiristy. Also Mac OS's native VPN support works aswel. I want to see what the windows VPN app is doing sothat I can try and mimic it in Ubuntu.

Thanks for any advice!

Rudolf

---

### Post by cwaldbieser on 2007-11-06
If the VPN is the typical Microsoft VPN (PPTP), you can get pptpconfig from the repositories (a useful VPN front end).

---

### Post by RudolfMDLT on 2007-11-07
> **cwaldbieser said:**
> If the VPN is the typical Microsoft VPN (PPTP), you can get pptpconfig from the repositories (a useful VPN front end).


Can a VPN be IPSec and PPTP?

---

### Post by cwaldbieser on 2007-11-07
> **RudolfMDLT said:**
> Can a VPN be IPSec and PPTP?

To be honest, I am not sure.  I don't really know much about IPSec other than it is a lower level protocol (level 3 OSI) used to secure higher level protocls (like TCP).

---

