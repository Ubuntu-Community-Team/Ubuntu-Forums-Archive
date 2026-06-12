---
title: "pam_mount can't retrieve password from PAM"
date: 2007-04-25
forum: General Help
---

### Post by make on 2007-04-25
I've always used pam_mount without issues under other distros, such as Mandriva, SuSE and others. But under Ubuntu Feisty 64-bit it just doesn't start working.

I've already successfully configured PAM to use LDAP (corporate network) and been googling for several days about pam_mount, testing everything I've found, reading every possible man-page and doc. Every possible combination of the configuration files for PAM. Nothing works. "tail /var/log/auth.log" still says "pam_mount can't read password from PAM". Even if I set it to ask for password if needed ("try_first_pass" instead of "use_first_pass"), it still fails reading it. I am (naturally) loading pam_mount.so before any modules tagged "sufficient" and as an auth-module (also tried session).

Can someone post a working configuration for Feisty + PAM + pam_mount? Or is the module simply broken in the 64-bit Feisty?

---

