---
title: "Samba LDAP string_to_sid error"
date: 2008-06-11
forum: General Help
---

### Post by ldarby on 2008-06-11
This is to help any one else who is in my situation.
I have a LDAP / Samba domain with several member servers.  For some time I have had problems with group name resolution on the member servers.  I get the error "string_to_sid: SID @<groupname> does not begin with `S-`"
ON a whim, I looked up the group sid with smbldap-groupshow and typed it into the permissions block of the smb.conf for a share.
I don't know what compatability problems this might cause in the future, but for now it fixed my problem., and the system shares files much faster.  I was also able to uninstall winbind completely since all the samba and unix authentication is done directly with LDAP.

---

