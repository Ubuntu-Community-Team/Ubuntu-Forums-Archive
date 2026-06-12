---
title: "kerberos multi-user CIFS mount I/O error at expiry despite having new TGT"
date: 2016-11-23
forum: General Help
---

### Post by keithward on 2016-11-23
Hi All,

I'm wondering if anyone has any suggestions to help on this one, as I'm running low on ideas.

I currently have a CIFS v3.02 mount , using kerberos authentication with the multiuser option enabled, this means any user logging in accesses the CIFS mount as their own AD user account, and not the machine account which initially mounted the share.

This setup works reasonably well, however I have a problem once it hits the TGT expiry, as the mount ceases to function (I/O Error, kernel log shows STATUS_NETWORK_SESSION_EXPIRED), this is despite having k5start daemon running in the background that continually regenerates a TGT as the old one expires.

It appears that the kernel gets latched onto the old (expired) TGT - and never bothers to check if the Kerberos caches has been updated? more importantly it appears that cifs.upcall doesn't appear to get called at all beyond the initial mount request (is this correct behavior?).

This is using Xenial - kernel 4.4.0-47.68

Keith

---

