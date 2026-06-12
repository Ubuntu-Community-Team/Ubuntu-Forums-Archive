---
title: "Vmware Server and LDAP"
date: 2007-03-22
forum: General Help
---

### Post by cnb2412 on 2007-03-22
Hi,

I've  a Problem with VMware-server an ldap.

I've a working ldap server providing user information as backend for pam. Now I'm trying to auth via a vmware service,but either mui or client works. I got the following message in my auth.log

Mar 23 01:20:56 localhost vmware-authd[12638]: PAM unable to dlopen(/lib/security/pam_ldap.so)
Mar 23 01:20:56 localhost vmware-authd[12638]: PAM [error: /lib/security/pam_ldap.so: cannot open shared object file: No such file or directory]
Mar 23 01:20:56 localhost vmware-authd[12638]: PAM adding faulty module: /lib/security/pam_ldap.so


My /etc/pam.d/vmware-authd contains the following lines:
#%PAM-1.0
auth    sufficient      pam_ldap.so
auth       required         /usr/local/lib/vmware/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok
account sufficient      pam_ldap.so
account    required         /usr/local/lib/vmware/lib/libpam.so.0/security/pam_unix_acct.so

Anny ideas?

---

### Post by cr3 on 2007-04-09
I have encountered the same problem when running VMware server 1.0.2 on Dapper. If this could be of any help, it seems that VMware server is using it's only pam library:

/usr/lib/vmware/lib/libpam.so.0/libpam.so.0.81.2

As can be seen from the filename, the pam library used seems to be 0.81.2 whereas Dapper uses this library:

/lib/libpam.so.0.79

So, the versions seem to differ significantly. This might explain why VMware server cannot use the system pam_ldap shared object. However, that doesn't provide a solution to enabling VMware to actually authenticate against LDAP.

---

