---
title: "SLOW LDAP Authentication."
date: 2016-05-04
forum: General Help
---

### Post by Slicster on 2016-05-04
Hi Guys,
We're currently experiencing slow LDAP authentication with our Ubuntu devices.  It works, but very slow and if our LDAP is down or unreachable, even the local authentication is slow, so slow that it may timeout.

Here is our configuration of LDAP.conf
> 
base DC=hello,DC=com
uri ldap://ldap.hello.com
ldap_version 3
rootbinddn cn=LDAP,ou=Users,dc=hello,dc=com
scope sub
pam_password md5
nss_base_passwd dc=hello,dc=com?sub?memberOf=CN=FWAdmins,OU=Network,OU=Groups,DC=hello,DC=com
nss_base_passwd dc=hello,dc=com?sub?memberOf=CN=FWSupport,OU=Network,OU=Groups,DC=hello,DC=com
nss_base_group  dc=hello,dc=com?sub
nss_base_shadow dc=hello,dc=com?sub


nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_objectclass posixGroup group
nss_map_attribute uniqueMember member
nss_map_attribute cn sAMAccountName
pam_login_attribute sAMAccountName


nss_initgroups_ignoreusers backup,bin,daemon,dhcpd,dnsmasq,games,gnats,irc,libuuid,list,lp,mail,man,messagebus,mysql,news,ntp,openldap,postfix,proxy,root,sshd,sync,sys,syslog,uucp,whoopsie,www-data




If I'm connected with any user and I perform the command "id username" it takes anywhere between 60-240 seconds.

It is confirmed that there are no network performance issues or high latency to be causing this. 

Any ideas?

---

