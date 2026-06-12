---
title: "Clarification of: kdc = kdcserver"
date: 2013-01-25
forum: General Help
---

### Post by DCalabrese on 2013-01-25
Following a previous thread:  [http://ubuntuforums.org/showthread.php?t=2050668:](http://ubuntuforums.org/showthread.php?t=2050668:)

[B] = {
        kdc = kdcserver [/B]       # kdcserver is full dns name of realm server same as domain server , or ip address can be also A.B.C.D
        [B]default_domain = yourdomain.local
    }

Does this mean:
[/B]
[B]= {
        kdc = kdcserver [/B]       # our IP
        [B]default_domain = ourdomain.local
    }

Thanks in advance for excellent help.  Chris
[/B]

---

