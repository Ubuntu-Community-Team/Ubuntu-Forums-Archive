---
title: "Update failed with 403 error..."
date: 2008-01-18
forum: General Help
---

### Post by a1user on 2008-01-18
"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

on no

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  403 Forbidden

---

### Post by PinkFloyd102489 on 2008-01-18
It's been submitted to Launchpad as a bug. It's the new xserver-org-core.

---

### Post by a1user on 2008-01-18
excellent, ty

---

### Post by PinkFloyd102489 on 2008-01-18
Anytime. I had a problem with it earlier at school. Usually when repo packages 403, it means they've been held back for some reason or another.

---

### Post by ccfisch on 2008-01-18
had the same problem with the i386 .deb. this seems like just a file permissions problem on a key piece of software -- so it should be solved quickly, right ?

---

### Post by PinkFloyd102489 on 2008-01-18
No the package is broken. Interferes with Java somehow I dont remember exactly.

---

