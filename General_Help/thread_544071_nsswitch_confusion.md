---
title: "nsswitch confusion"
date: 2007-09-05
forum: General Help
---

### Post by tiger74 on 2007-09-05
Hello all,
I'm stumpped here. I use my ubuntu to be authenticated to a LDAP server. It 
works.

However, if the connection to the LDAP server is not available (such as when I unplug the network cable), **I cannot logon at all**. Shouldn't I can still be able to logon using my 'local' account in /etc/passwd?

The /etc/nsswitch.conf is:
passwd:         files ldap
group:            files ldap
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Thank you.
-- 
Fajar Priyanto | Reg'd Linux User #327841 | Linux tutorial 
[http://linux2.arinet.org](http://linux2.arinet.org)
08:54:24 up 16 min, 2.6.20-16-generic GNU/Linux 
Let's use OpenOffice. [http://www.openoffice.org](http://www.openoffice.org)

---

