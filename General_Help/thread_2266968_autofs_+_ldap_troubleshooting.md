---
title: "autofs + ldap troubleshooting"
date: 2015-02-26
forum: General Help
---

### Post by jakub16 on 2015-02-26
Hello,

I am new to LDAP and today I have been strugling with getting it work with already working autofs. I have been following this guide here:

[https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)

I used phpldapadmin for populating the database, here is my export:

> # Entry 1: ou=LDAPadmin,dc=pi,dc=com
dn: ou=LDAPadmin,dc=pi,dc=com
objectclass: organizationalUnit
objectclass: top
ou: LDAPadmin

# Entry 2: ou=automount,ou=LDAPadmin,dc=pi,dc=com
dn: ou=automount,ou=LDAPadmin,dc=pi,dc=com
objectclass: organizationalUnit
objectclass: top
ou: automount

# Entry 3: ou=auto.master,ou=automount,ou=LDAPadmin,dc=pi,dc=com
dn: ou=auto.master,ou=automount,ou=LDAPadmin,dc=pi,dc=com
objectclass: automountMap
objectclass: top
ou: auto.master

# Entry 4: cn=/mnt/nfs/,ou=auto.master,ou=automount,ou=LDAPadmin,dc=pi,dc...
dn: cn=/mnt/nfs/,ou=auto.master,ou=automount,ou=LDAPadmin,dc=pi,dc=com
automountinformation: ldap:ou=auto.network,ou=automount,ou=LDAPadmin,dc=pi,d
 c=com --timeout=60 --ghost
cn: /mnt/nfs/
objectclass: automount
objectclass: top

# Entry 5: ou=auto.network,ou=automount,ou=LDAPadmin,dc=pi,dc=com
dn: ou=auto.network,ou=automount,ou=LDAPadmin,dc=pi,dc=com
objectclass: automountMap
objectclass: top
ou: auto.network

# Entry 6: cn=server,ou=auto.network,ou=automount,ou=LDAPadmin,dc=pi,dc=c...
dn: cn=server,ou=auto.network,ou=automount,ou=LDAPadmin,dc=pi,dc=com
automountinformation: server -fstype=nfs,rw,soft,intr,async,vers=3 192.168.0
 .107:/media/usb/
cn: server
objectclass: automount
objectclass: top

I needed to patch autofs with this, since there was a bug:
[https://launchpad.net/ubuntu/+source/autofs/5.0.7-3ubuntu3](https://launchpad.net/ubuntu/+source/autofs/5.0.7-3ubuntu3) (there was some problems with lookup_ldap.so or something similiar like that).

The problem is, it is not functioning now when I added LDAP option. I double checked everything, tried to see syslog for help, but there is only this:

Starting automounter version 5.0.7, master map /my_ip:/ou=auto.master,ou=automount,ou=LDAP admin,dc=pi,dc=com
using kernel protocol version 5.02
no mounts in table

I tried to search for something, but with no usefull results, NFS was working perfectly before I added LDAP. There must be something wrong, but I cant find what, where...

Please, can someone help me? I would really apprectiate it >_<

EDIT: 

I managed to fix that error, now I am able to see my ghosted folder in my directory, but I cannot access it.

> starting automounter version 5.07, master map .....
using kernel protocool version 5.02
mounted indirect on /mnt/nfs with timeout 60, freq 15 seconds
ghosting enabled
attempting to mount entry /mnt/nfs/.hidden
key ".hidden" not found in map source(s).
dailed to mount /mnt/nfs/.hidden
attempting to mount entry /mnt/nfs/server
failed to mount /mnt/nfs/server

---

