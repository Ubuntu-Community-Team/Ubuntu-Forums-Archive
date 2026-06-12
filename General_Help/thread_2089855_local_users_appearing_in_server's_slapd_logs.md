---
title: "local users appearing in server's slapd logs"
date: 2012-11-30
forum: General Help
---

### Post by N-t-F on 2012-11-30
Hello,

although my setup happens to work, various issues intrigue me, and I don't even know if they are related. Here is one of them.

My setup:

-> Ubuntu 12.04 (64b) clients running xfce ("xubuntu-desktop" package) and using pam-ldapd and libdnss-ldapd.
-> A Debian Squeeze server providing NFS home directories, and OpenLDAP for authenticating users. The server is also its own client, so that rights are understandable in exported home directories.

The first problem I see is that local users from both server and clients apparently try to authenticate through LDAP. Anyway, requests are recorded in the logs for their homeDirectory, uidNumber and other things. This includes cron, root, lightdm, debian-exim, www-data and local regular users accounts (from /etc/passwd and /etc/shadow). As far as I understand things, they should never even appear in slapd logs, should they? :confused: For the record, my /etc/nsswitch.conf is as follows:
```
passwd: files ldap
group: files ldap
shadow: files ldap

```

And /etc/pam.d/common-auth is as follows:

```
# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_ldap.so minimum_uid=1000 use_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_cap.so 
# end of pam-auth-update config

```

So, is this normal and, if not, does anyone please have an idea regarding the problem?

---

