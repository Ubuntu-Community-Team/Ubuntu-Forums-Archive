---
title: "Likewise - Active Directory"
date: 2008-04-30
forum: General Help
---

### Post by tummen on 2008-04-30
Hey

Im pretty new to ubuntu but thought i would give it a go at my work.
(installed the 8.04 version of ubuntu today)

Having problem getting to join the domain at work (win2003server)

Installed likewise but it gives me this error when trying to join domain:

Error code: CENTERROR_DOMAINJOIN_JOIN_FAILED (0x0008000e)

Backtrace:
    main.c:310
    djmodule.c:264
    djauthinfo.c:825

Using the administrator login (that i know is correct) 

Anyone wanna give me some hints to what i have done wrong or what i am missing to do?

Best regards

Andreas

---

### Post by inselaffe on 2008-04-30
Are you using the FQDN for the domain? i.e. use DOMAIN.COM not DOMAIN

---

### Post by tummen on 2008-05-01
Hi

Our domain is vbs (vbs.local) but i cant use that because it says it cant dns it. So i tried using server instead, perhaps that is the error i dont know.

---

