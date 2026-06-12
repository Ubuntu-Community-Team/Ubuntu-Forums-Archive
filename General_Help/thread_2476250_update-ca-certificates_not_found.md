---
title: "update-ca-certificates not found"
date: 2022-06-21
forum: General Help
---

### Post by zentian on 2022-06-21
I'm trying to install a ca certificate and when I run update-ca-certificates, I get command not found. I've tried apt-get install ca-certificate, but it says it can't find a package by that name. How do I install update-ca-certificates?

---

### Post by deadflowr on 2022-06-21
The package is ca-certificates, not ca-certificate.
Which makes sense as it installs a multitude of certificates and not just one.
Seems odd that you wouldn't already have them though.

Also, have you upgraded the system to a supported release, based on your prior thread here:
[https://ubuntuforums.org/showthread.php?t=2476021]("https://ubuntuforums.org/showthread.php?t=2476021")
Which you states the host as being 21.04.

---

