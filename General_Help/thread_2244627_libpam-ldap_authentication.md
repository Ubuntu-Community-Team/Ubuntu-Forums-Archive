---
title: "libpam-ldap authentication"
date: 2014-09-17
forum: General Help
---

### Post by sherrera on 2014-09-17
Hello,

I am running Ubuntu 12.04 using libpam-ldap using netgroups that are defined in ldap. The authentication works great but when I try to upgrade to 14.04, it breaks. While on 14.04, I run a finger -m username on a user in my netgroup and it retrieves information from LDAP just fine. I run it against a user not in my netgroup and it fails, as it should. Currently it only allows the local user to log in.  When setting up libpam-ldap in 12.04, I only modified the /etc/passwd (to add netgroup), /etc/nsswitch.conf (to add [COLOR=#000000][FONT=Arial]passwd_compat:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]ldap and change netgroup: ldap)[/FONT][/COLOR] and /etc/pam.d/common-session (to autocreate home directory on login). Everything else stayed default. 

It seems as though there is a config somewhere that I haven't found that seems to deny everyone except local users. What changed in this package from 12.04 package? 

Any help is appreciated.

Thanks

---

### Post by sherrera on 2014-09-18
If i change my /etc/ldap.conf file to use uri ldap://ldapserver  it will work, but if I use uri ldaps://ldapserver it fails. ldaps is preferred for security of not sending plaintext passwords. In my /var/log/auth.log file when I have it set to ldaps and use a non local account I get nss_ldap:failed to bind to LDAP server ldaps.  

Any thoughts?

---

### Post by sherrera on 2014-09-19
I think I found the issue.  I found this in the auth.log: nss_ldap: could not connect to any LDAP server as (null).  Is there a command that I can run on the commandline to test this?  I have tested using ldapsearch with the -x as an anonymous user and it works as expected. The only configs I have in the /etc/ldap.conf are search base, uri ldaps://ldap fqdn, ldap_version 3 and pam_password md5. 

I'm sure the problem is in this file but I don't know how else to test the way it is communicating to ldap.

---

### Post by sherrera on 2014-09-22
Solved:  In the /etc/nsswitch.conf file I have previously only had to use compat for passwd  now with ubuntu 14 it looks like i'm required to use files compat with passwd. ie
 
passwd:        files compat
passwd_compat:  ldap

---

