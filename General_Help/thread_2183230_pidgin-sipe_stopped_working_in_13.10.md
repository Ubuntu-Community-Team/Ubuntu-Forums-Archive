---
title: "pidgin-sipe stopped working in 13.10"
date: 2013-10-24
forum: General Help
---

### Post by Robin_Heggelund_Hansen on 2013-10-24
As the title says, after upgrading to 13.10, pidgin-sipe stopped working. On login I now get an error message regarding a ssl certificate or something like that. It worked perfectly on 13.04. Anyone else have problems, or know of a fix?

---

### Post by daitau on 2013-11-01
Not sure if we had the same issue, but this fixed the problem for me after upgrading to 13.10: [http://sourceforge.net/p/sipe/wiki/Frequently%20Asked%20Questions/#after-upgrading-to-sipe-1150-40or-newer41wzxhzdk4pidgin-fails-with-failed-to-authenticate-to-server]("http://sourceforge.net/p/sipe/wiki/Frequently%20Asked%20Questions/#after-upgrading-to-sipe-1150-40or-newer41wzxhzdk4pidgin-fails-with-failed-to-authenticate-to-server")

> **Robin_Heggelund_Hansen said:**
> As the title says, after upgrading to 13.10, pidgin-sipe stopped working. On login I now get an error message regarding a ssl certificate or something like that. It worked perfectly on 13.04. Anyone else have problems, or know of a fix?

---

### Post by aril-spetalen on 2013-11-14
I just tried the workaround setting
export NSS_SSL_CBC_RANDOM_IV=0
e.g. in the /etc/default/pidgin-sipe file, after getting this problem when upgrading from 13.04 toi 13.10. 

However, I still encounter the problem, and now additionally, AIM connection is broken.. :-/

---

### Post by Baromur on 2014-01-09
I had similar problem, after upgrading from 13.04 to 13.10 independently if the NSS_SSL_CBC_RANDOM_IV was set or not. The solution for me was the disable the single sign on in the account properties.

---

