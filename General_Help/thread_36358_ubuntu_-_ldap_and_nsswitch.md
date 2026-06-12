---
title: "ubuntu - ldap and nsswitch"
date: 2005-05-23
forum: General Help
---

### Post by alpertc on 2005-05-23
I am running openldap on my Ubuntu system and it all seems to be working fine having installed libpam-ldap and libnss-ldap.

The problem I am seeing is that when a user auhenticates against the system (password or ldap user) they are prompted twice for their account password. It seems the first attempt fails but the second one works.

Any pointers?

---

### Post by nocturn on 2005-05-23
[QUOTE=alpertc]I am running openldap on my Ubuntu system and it all seems to be working fine having installed libpam-ldap and libnss-ldap.

The problem I am seeing is that when a user auhenticates against the system (password or ldap user) they are prompted twice for their account password. It seems the first attempt fails but the second one works.

Any pointers?[/QUOTE]

What is in your PAM files?

---

### Post by alpertc on 2005-05-23
I have added  "sufficient pam_ldap.so" above the existing entries in the following files:
common-account
common-auth
common-password
common-session
sudo

e.g.
#%PAM-1.0

@include common-auth
@include common-account

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so


and my nsswitch looks like this

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         ldap [NOTFOUND=continue] files
group:          ldap [NOTFOUND=continue] files
shadow:         ldap [NOTFOUND=continue] files

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

---

### Post by MaskedMarauder on 2005-10-12
So, where do I get a libpam-ldap for Breazy?  It doesn't appear to be anywhere I've looked so far.  I hope it's included with the final release.

BTW, anyone know why mod_authz_ldap won't compile on ubuntu?

---

