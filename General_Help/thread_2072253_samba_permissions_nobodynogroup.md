---
title: "samba permissions nobody/nogroup"
date: 2012-10-17
forum: General Help
---

### Post by itninjasteve on 2012-10-17
I am running Ubuntu 12.04 using winbind to connect to an Windows 2008 AD server.  I use autofs to map the home directories, the only problem is the permissions are reading nobody nogroup.  Does anyone have any idea what I'm doing wrong?  This worked in 10.10


Here are my config files.  Let me know if you want to look at anything else.

smb.conf
-------
[global]
   security = ads
   realm = domain.com
   password server = pdc.domain.com bdc.domain.com
   workgroup = DOMAIN
   idmap config * : backend = tdb
   idmap config * : range = 10000-20000
   idmap config DOMAIN : backend  = rid
   idmap config DOMAIN : range = 10000-20000
   idmap config DOMAIN : base_rid = 0
   winbind enum users = yes
   winbind enum groups = yes
   winbind refresh tickets = yes
   template homedir = /vhome/%U
   template shell = /bin/bash
   client use spnego = yes
   client ntlmv2 auth = yes
   encrypt passwords = yes
   winbind use default domain = yes
   restrict anonymous = 2



auto.master
--------
+auto.master
/vhome    /etc/auto.vhome




/etc/auto.vhome 
--------
* -fstype=nfs4,rw,hard,intr       nfs.domain.com:/&

---

### Post by itninjasteve on 2012-10-29
Any ideas?

Thank you in advance!

---

### Post by luvshines on 2012-11-16
Does id command or wbinfo command for the users return correct UID/GID ?

---

