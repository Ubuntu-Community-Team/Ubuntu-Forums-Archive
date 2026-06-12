---
title: "RDP client with MFA."
date: 2022-05-07
forum: General Help
---

### Post by prakhars962 on 2022-05-07
My university supplies rdp files to connect to library PCs. They have enabled MFA, so I have to allow on Microsoft Authenticator each time I connect. I am looking for RDP client that supports MFA. Remmina and others do not support this even in 2022. Somebody asked the same question in 2016 on this forum. I use Ubuntu 20.04 LTS.

---

### Post by TheFu on 2022-05-08
If it were me, I'd take a laptop into the library and ask for help, but don't mention Linux or Ubuntu.  Let them see your system and freak out just a bit.  See of more people there can't be pulled into the problem. Even if they can't solve the issue, it will be much clearer to them that MSFT isn't the only OS and that real people have real issues with proprietary solutions.

Google found this solution from a MSFT forum where 4 other workarounds for MFA+RDP failed:
> providing both gateway and broker (without settings DefaultTsvUrl and providing load-balance-info) = Working (with MFA)

I don't know anything about Microsoft Authenticator or what DefaultTsvUrl means, but perhaps it is enough of a lead?  The desktop was using Ubuntu.

---

