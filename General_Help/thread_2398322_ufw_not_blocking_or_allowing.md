---
title: "ufw not blocking or allowing?"
date: 2018-08-10
forum: General Help
---

### Post by ulao3 on 2018-08-10
To                         Action      From
--                         ------      ----
443/tcp                    ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
443/tcp (v6)               ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)


yet
**PORT    STATE  SERVICE**


21/tcp  **closed **ftp

22/tcp  **open **  ssh

80/tcp  **open **  http

443/tcp **closed **https

Its like there is something else blocking, but this is a fresh install of 18.04

---

### Post by steeldriver on 2018-08-10
Do you actually have any services listening on ports 21 or 443

---

### Post by ulao3 on 2018-08-10
That was the issue, I though 443 was on for sure.

---

