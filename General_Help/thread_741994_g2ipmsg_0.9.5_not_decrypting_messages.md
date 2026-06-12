---
title: "g2ipmsg 0.9.5 not decrypting messages"
date: 2008-04-01
forum: General Help
---

### Post by mianda_psi on 2008-04-01
I have recently installed g2ipmsg 0.9.5 and sometimes when someone using the windows program ipmsg sends me a message I get the following 2 errors:

Can not decode message from {sender ip} rc = -2
Can not convert message from {sender ip} into ineternal representation

Any help would b greatly appreciated.

---

### Post by takeharu on 2008-04-28
Hi, 

As far as I think, you can not use blowfish on your site.
Please rebuild g2ipmsg without ssl support at this time.
I'll add encryption algorithm chooser in next release.

> **mianda_psi said:**
> I have recently installed g2ipmsg 0.9.5 and sometimes when someone using the windows program ipmsg sends me a message I get the following 2 errors:

Can not decode message from {sender ip} rc = -2
Can not convert message from {sender ip} into ineternal representation

Any help would b greatly appreciated.

---

