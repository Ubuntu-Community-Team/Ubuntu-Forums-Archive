---
title: "xUbuntu LDAP Client"
date: 2006-12-01
forum: General Help
---

### Post by sgeberl on 2006-12-01
Sorry but I do have serious problems installing a xUbuntu as LDAP - Client. With the mentioned configuration I'am not able to login via  desktop - manager (but login via shell works). The Problem can be solved by additionally installing the UBUNTU Gnome - desktop - meta-package. but I think, there must be a better solution. Maybe I forgot to install something that is installed  automatically with the Gnome meta-package. Any ideas please?

Thanks Stephan.


Configuration - Detail (I startet at a bare xUbuntu Instalation)
Samba – Client und LDAP
```
apt-get install
	libsmbclient
	smbclient
	samba-common
	ldap-utils	(Command – Line Utilities)
```
/etc/ldap/ldap.conf
```
BASE  dc=vip-beratung, dc=local
URI ldap://192.168.10.20
SIZELIMIT  12
TIMELIMIT  15
DEREF      never
```
/etc/samba/smb.conf
```
[global]
   workgroup = vip-beratung
   security = DOMAIN
   local master = no
   wins support = no
   panic action = /usr/share/samba/panic-action %d
```

```
net join ads –w vip-beratung
apt-get install
	libnss-ldap
	libpam-ldap
```
/etc/libnss-ldap.conf
```
host 192.168.10.20
base dc=vip-beratung,dc=local
# rootbinddn cn=admin,dc=vip-beratung,dc=local  # meist nicht gesetzt!
ldap_version 3
```
Konfiguration: (Kontrolle!) /etc/pam_ldap.conf
```
host 192.168.10.20
base dc=vip-beratung,dc=local
# rootbinddn cn=admin,dc=vip-beratung,dc=local – anonym!
ldap_version 3
pam_password crypt    # meist nicht gesetzt!
```
SAMBA
```
apt-get install
	smbfs
	libpam-mount
```
/etc/nsswitch.conf
```
# /etc/nsswitch.conf
passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files dns mdns
bootparams:     nisplus [NOTFOUND=return] files
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netmasks:       db files

netgroup:       nis files
publickey:      nisplus
```
/etc/pam.d/common-pammount
```
# include this file after common-auth and after common-session with
# @include common-pammount
auth       optional   pam_mount.so use_first_pass
session    optional   pam_mount.so use_first_pass
```
/etc/pam.d/common-password
```
# /etc/pam.d/common-password - password-related modules common to all services
# Check local authentication first, so root can still login
# while LDAP is down.
# password required                  pam_unix.so nullok obscure min=4 max=8 md5
password  [success=1 default=ignore] pam_unix.so use_first_pass nullok obscure min=4 max=8 md5
password  required                   pam_ldap.so use_first_pass
password  required                   pam_permit.so
```
/etc/pam.d/common-session
```
# /etc/pam.d/common-session - session-related modules common to all services
# Check local authentication first, so root can still login
# while LDAP is down.
# session   required                     pam_unix.so
session     [success=3 default=ignore]   pam_unix.so
session     required                     pam_ldap.so use_first_pass
auth        optional                     pam_mount.so use_first_pass
session     optional                     pam_mount.so use_first_pass
session     required                     pam_permit.so
session     optional                     pam_foreground.so
```
/etc/pam.d/common-auth
```
# /etc/pam.d/common-auth - authentication settings common to all services
# Check local authentication first, so root can still login
# while LDAP is down.
# auth  required                        pam_unix.so nullok_secure
auth    [success=3 default=ignore]      pam_unix.so nullok_secure
auth    required                        pam_ldap.so use_first_pass
auth    optional                        pam_mount.so use_first_pass
session optional                        pam_mount.so use_first_pass
auth    required                        pam_permit.so
```
/etc/pam.d/common-account
```
# /etc/pam.d/common-account - authorization settings common to all services
# Try local /etc/shadow first and skip LDAP on success
# account required                     pam_unix.so
account   [success=1 default=ignore]   pam_unix.so
account   required                     pam_ldap.so use_first_pass
account   required                     pam_permit.so
```

```
/etc/security/pam_mount.conf (not the full)
# Turn on if you want to debug why some volume cannot be mounted etc.
# This can be overriden by user's local configuration
# 
# Format: debug [ 1 | 0 ]
# Local user configuration can override this.

debug 1
mkmountpoint 1
... usw.
```

---

