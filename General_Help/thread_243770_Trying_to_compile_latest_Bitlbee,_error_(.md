---
title: "Trying to compile latest Bitlbee, error :("
date: 2006-08-25
forum: General Help
---

### Post by Poka64 on 2006-08-25
Trying to compile the latest stable bitlbee release, 1.0.3 but I'm getting this when try to:

```
BitlBee configure

ERROR: Could not find a suitable SSL library (GnuTLS, libnss or OpenSSL).
       This is necessary for MSN and full Jabber support. To continue,
       install a suitable SSL library or disable MSN support (--msn=0).
       If you want Jabber without SSL support you can try --ssl=bogus.

```

Looking through my installed packages and I think I have OpenSSL and all of the other packages installed :(

I'm using ubuntu dapper.

---

### Post by ato on 2006-08-25
libssl-dev is installed?

---

### Post by Poka64 on 2006-08-25
> **ato said:**
> libssl-dev is installed?

well, I used libgnutls-dev instead, compiled it succesfully, but I can't connect so I'm back on 1.0.1 for now.

---

