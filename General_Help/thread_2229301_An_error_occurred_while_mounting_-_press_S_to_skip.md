---
title: "An error occurred while mounting - press S to skip or M for manual recovery"
date: 2014-06-12
forum: General Help
---

### Post by gb10hkzo-fb on 2014-06-12
Because of the curious decision taken by the guys at Courier that they would not provide a way to specify a socket directory in the conf, I've been trying to follow suggestions elsewhere on the internet saying that adding :

```
/var/run/courier /var/spool/postfix/var/run/courier none bind 0 0
```

Should do the trick to getting it work in chroot.

The postfix sub-directory exists, and if mounted manually it works (although "df" shows /run/courier in the left hand column instead of /var/run/courier).

Any ideas ?

---

