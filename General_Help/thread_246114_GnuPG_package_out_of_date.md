---
title: "GnuPG package out of date"
date: 2006-08-28
forum: General Help
---

### Post by TrinitronX on 2006-08-28
Is there a reason that ubuntu is still using GPG version 1.4.2.2 as opposed to the latest release 1.4.5?
Any way to get this updated if plausible?

---

### Post by skymt on 2006-08-28
1.4.2 was the latest version when Dapper was released.

---

### Post by yopnono on 2006-08-29
Maybe they should provide a new ver of it. Since it has some flaws.
 ```
1.4.5
* Fixed 2 more possible memory allocation attacks.  They are
 similar to the problem we fixed with 1.4.4.  This bug can easily
 be be exploted for a DoS; remote code execution is not entirely
 impossible.

 1.4.4
* User IDs are now capped at 2048 byte.  This avoids a memory
  allocation attack (see CVE-2006-3082).
```

---

### Post by raindog on 2006-11-13
I too don't understand why the gnupg package hasn't been updated.

---

### Post by mingotta on 2007-08-31
This is such a pain in the ***. Gnupg version 1.4.7 has been out for quite a while now but the ubuntu repositories still haven't been updated to include it!! It's driving me mad!

---

### Post by nixclusive on 2007-10-27
Yeah me too.. even after upgrading to gutsy the gnupg package is still stagnant at 1.4.6 even the version 1.4.7 has been around for quite a while. The maintainers being listed as "Ubuntu Core Developers". I wonder what's keeping them back as gnupg is an integral part of the package authentication system.

---

