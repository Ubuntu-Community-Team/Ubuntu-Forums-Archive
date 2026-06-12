---
title: "autofs via ldap - &quot;init gathered global options: (null)&quot;"
date: 2013-02-21
forum: General Help
---

### Post by egorks on 2013-02-21
hi all!

i am sort of ldap novice, so please if someone could tell me what am i doing wrong. 

have over 10 PCs on opensuse working with the same ldap server using host resolution, users and autofs mounts. but when i tried to set up ubuntu server 12.10 with autofs i get following output (host resolution on the same machine works fine):
```
Feb 20 20:33:54 term03 automount[26137]: Starting automounter version 5.0.6, master map nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch
Feb 20 20:33:54 term03 automount[26137]: using kernel protocol version 5.02
Feb 20 20:33:54 term03 automount[26137]: lookup_nss_read_master: reading master ldap nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch
Feb 20 20:33:54 term03 automount[26137]: parse_init: parse(sun): init gathered global options: (null)
Feb 20 20:33:54 term03 automount[26137]: no mounts in table
```here is the ldif dump from the server for autofs part:

```
dn: ou=autofs,dc=cpsag,dc=ch
objectClass: organizationalUnit
ou: autofs
structuralObjectClass: organizationalUnit
entryUUID: 5bb5e5d8-1ab5-102e-976c-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811112503Z
entryCSN: 20090811112503.374038Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20090811112503Z

dn: nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch
objectClass: top
objectClass: nisMap
nisMapName: auto.master
structuralObjectClass: nisMap
entryUUID: 6f01849c-1ac6-102e-978d-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132717Z
entryCSN: 20090811132717.190734Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20090811132717Z

dn: cn=/nfs02,nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: /nfs02
nisMapName: auto.master
structuralObjectClass: nisObject
entryUUID: 6f02fe6c-1ac6-102e-978e-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132717Z
nisMapEntry: ldap:auto.nfs02 --timeout=60
entryCSN: 20110201203019.112433Z#000000#000#000000
modifiersName:
modifyTimestamp: 20110201203019Z

dn: nisMapName=auto.nfs02,ou=autofs,dc=cpsag,dc=ch
objectClass: top
objectClass: nisMap
nisMapName: auto.nfs02
structuralObjectClass: nisMap
entryUUID: 73952798-1ac6-102e-978f-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132724Z
entryCSN: 20090811132724.869173Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20090811132724Z

dn: cn=home,nisMapName=auto.nfs02,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: home
nisMapName: auto.nfs02
structuralObjectClass: nisObject
entryUUID: 7395408e-1ac6-102e-9790-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132724Z
nisMapEntry: nul
entryCSN: 20120720143945.362625Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20120720143945Z

dn: cn=export,nisMapName=auto.nfs02,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: export
nisMapName: auto.nfs02
structuralObjectClass: nisObject
entryUUID: 739565dc-1ac6-102e-9791-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132724Z
nisMapEntry: nul
entryCSN: 20120720143929.427328Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20120720143929Z

dn: cn=misc,nisMapName=auto.nfs02,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: misc
nisMapName: auto.nfs02
structuralObjectClass: nisObject
entryUUID: 7395826a-1ac6-102e-9792-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811132724Z
nisMapEntry: nul
entryCSN: 20120720143958.718676Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20120720143958Z

dn: cn=cpsteam,nisMapName=auto.nfs02,ou=autofs,dc=cpsag,dc=ch
cn: cpsteam
nisMapName: auto.nfs02
objectClass: nisObject
structuralObjectClass: nisObject
entryUUID: 52f99c02-1ac7-102e-9794-1512cbab8751
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20090811133339Z
nisMapEntry: -fstype=cifs,rw,perm,timeout=60,nocase,rsize=32768,wsize=32768,ui
 d=egor,gid=cps01,credentials=/etc/cpsteam ://192.168.65.12/cpsdata
entryCSN: 20110201204423.992837Z#000000#000#000000
modifiersName:
modifyTimestamp: 20110201204423Z

dn: cn=/nfs01,nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: /nfs01
nisMapName: auto.master
structuralObjectClass: nisObject
entryUUID: 2fefb288-170f-102f-968a-7bf2d225ebba
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20100628144257Z
nisMapEntry: ldap:auto.nfs01 --timeout=60
entryCSN: 20110201202915.111573Z#000000#000#000000
modifiersName:
modifyTimestamp: 20110201202915Z

dn: nisMapName=auto.nfs01,ou=autofs,dc=cpsag,dc=ch
objectClass: top
objectClass: nisMap
nisMapName: auto.nfs01
structuralObjectClass: nisMap
entryUUID: 451853d6-170f-102f-968b-7bf2d225ebba
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20100628144333Z
entryCSN: 20100628144333.157129Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20100628144333Z

dn: cn=home,nisMapName=auto.nfs01,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: home
nisMapName: auto.nfs01
structuralObjectClass: nisObject
entryUUID: 4518776c-170f-102f-968c-7bf2d225ebba
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20100628144333Z
nisMapEntry: -fstype=nfs,rw,timeo=60,soft,intr,rsize=32768,wsize=32768,nosuid 
 nfs01:/data/home
entryCSN: 20110202184724.796728Z#000000#000#000000
modifiersName:
modifyTimestamp: 20110202184724Z

dn: cn=export,nisMapName=auto.nfs01,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: export
nisMapName: auto.nfs01
structuralObjectClass: nisObject
entryUUID: 4518c4d8-170f-102f-968d-7bf2d225ebba
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20100628144333Z
nisMapEntry: -fstype=nfs,rw,timeo=60,soft,intr,rsize=32768,wsize=32768,nosuid 
 nfs01:/data/export
entryCSN: 20110907180124.187345Z#000000#000#000000
modifiersName: cn=Admin,dc=cpsag,dc=ch
modifyTimestamp: 20110907180124Z

dn: cn=misc,nisMapName=auto.nfs01,ou=autofs,dc=cpsag,dc=ch
objectClass: nisObject
cn: misc
nisMapName: auto.nfs01
structuralObjectClass: nisObject
entryUUID: 451b16de-170f-102f-968e-7bf2d225ebba
creatorsName: cn=Admin,dc=cpsag,dc=ch
createTimestamp: 20100628144333Z
nisMapEntry: -fstype=nfs,rw,timeo=60,soft,intr,rsize=32768,wsize=32768,nosuid 
 nfs01:/data/misc
entryCSN: 20110202184616.178380Z#000000#000#000000
modifiersName:
modifyTimestamp: 20110202184616Z

```and the config of the client machine:

```
MASTER_MAP_NAME="nisMapName=auto.master,ou=autofs,dc=cpsag,dc=ch"
TIMEOUT=300
NEGATIVE_TIMEOUT=20
BROWSE_MODE="yes"
MOUNT_NFS_DEFAULT_PROTOCOL=4
APPEND_OPTIONS="yes"
LOGGING="debug"
LDAP_URI="111.11.11.11"
SEARCH_BASE="ou=autofs,dc=cpsag,dc=ch"

```

why can it not parse the config?

---

### Post by egorks on 2013-03-01
hi all,

tried to change config on one of the shares but without luck.

can anyone help me?

---

### Post by schragge on 2013-03-01
Does mounting the NFS share from Ubuntu manually works? What does *showmount -e nfs01* show? And *rpcinfo -p nfs01*? Also, do you have the problem with autofs only on boot? Say if you *sudo -i -u some_user_with_automounted_home*, does user's home directory get automounted?

---

### Post by egorks on 2013-03-01
> **schragge said:**
> Does mounting the NFS share from Ubuntu manually works? What does *showmount -e nfs01* show? And *rpcinfo -p nfs01*? Also, do you have the problem with autofs only on boot? Say if you *sudo -i -u some_user_with_automounted_home*, does user's home directory get automounted?

manual mounting works. also if i put fstab entries i get it working just fine. problems only appear if i try to get automount info from ldap server, no parameters are being parced, from how it looks like... so if i try to access any of the supposedly automounted directories i get 'no such file or directory' error.


i presume maybe some schemas are not compatible between opensuse and ubuntu?

---

