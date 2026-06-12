---
title: "Deluged is crashing"
date: 2012-12-14
forum: General Help
---

### Post by evvdcaec on 2012-12-14
Ubuntu Server 12.04 LTS
Can someone decipher this (from syslog) for me and tell me if this has to do with why deluged is crashing after 5 minutes?

```
server kernel: [1289724.571151] deluged[25916]: segfault at 7f77cc293000 ip 00007f77de16afbd sp 00007f77da027370 error 4 in libcrypto.so.1.0.0[7f77de0e2000+19f000]
```

It starts fine and acts normal but it won't stay going.

---

### Post by evvdcaec on 2012-12-21
Thanks for all the help and suggestions guys.  Turns out the problem was with a corrupt download.  Whenever deluge would check the file contents it would crash.  I removed the offending file and it's been working fine for a few days.

---

