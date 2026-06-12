---
title: "Need files for shutdown and reboot"
date: 2008-06-11
forum: General Help
---

### Post by blackmachine on 2008-06-11
Hi guys.. I need to ask a favor.. can someone upload 2 files from sbin folder.
1) shutdown
2) reboot

I don't know what have gone wrong but, i notice that those 2 files are there but no where to be seen  :(

```
blackmachine@blackmachine-desktop:~$ which shutdown
/sbin/shutdown
blackmachine@blackmachine-desktop:~$ which reboot
/sbin/reboot

```

---

### Post by cmnorton on 2008-06-11
On what kind of Linux distro have you seen these files? The shutdown binary I found on Red Hat 9, and

/etc/pam.d/reboot
/etc/security/console.a
/usr/share/doc/nss_ldap
/usr/share/doc/pam_krb5
/usr/share/doc/pam_krb5

From a RH EL 4 system
/usr/share/doc/nss_ldap-226/pam.d/reboot
/etc/security/console.apps/reboot
/etc/pam.d/reboot

Also, I am reluctant to upload a binary to this site. Basically, you could re-create these as shell scripts using shutdown.

---

