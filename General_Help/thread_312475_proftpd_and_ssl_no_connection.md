---
title: "proftpd and ssl no connection"
date: 2006-12-04
forum: General Help
---

### Post by Primal-id on 2006-12-04
I'm receiving the following error in the tls.log:

```
Dec 04 12:14:18 mod_tls/2.1.1[5523]: SSL/TLS-P requested, starting TLS handshake
Dec 04 12:14:18 mod_tls/2.1.1[5523]: unable to accept TLS connection:
  (1) error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
Dec 04 12:14:18 mod_tls/2.1.1[5523]: SSL/TLS-P negotiation failed on control channel
```

Regular ftp works fine but with the ssl enabled i'm unable to connect. Could this be due to possibly needing to compile mod_tls? If so where do I find this at? I've been unable to locate it.

---

### Post by Primal-id on 2006-12-15
after further research i have found the following that may be the cause:
```
 Bug 2573 - TLSProtocol directive in proftpd.conf is ignored.  By fixing 
    this bug, sites may find that a mod_tls configuration which worked
    prior to 1.3.0rc1 now does not work, failing with an error like
    "wrong version number" appearing in the TLSLog.  To restore the previous
    behavior, these sites can use "TLSProtocol SSLv23" in proftpd.conf.
```

i'm thinking if i can some how use another mod_tls file but I don't have any idea where to find one or what it is. Does anyone have any suggestions or some where they could point me to get further clarification

---

