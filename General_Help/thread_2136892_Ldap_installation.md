---
title: "Ldap installation"
date: 2013-04-18
forum: General Help
---

### Post by Rakeshvijayan on 2013-04-18
Hi friends I am try to learn LDAP and samba installation on ubuntu 12.04 I got you tube video tutorial and i follwed the instruction that he give to me but when I to add samba user in PHPLDAPADMIN  commit button is not enabled I followed this link [https://www.youtube.com/watch?v=FzpzQNU-Iuc](https://www.youtube.com/watch?v=FzpzQNU-Iuc)[IMG]http://s11.postimg.org/sjtoldeqb/crate_samba.png[/IMG]


[IMG]http://s10.postimg.org/iitsy2vtl/create_button_not_enabled.png[/IMG]

 ```
   1   apt-get install slapd ldap-utils
 

 2 dpkg-reconfigure slapd
 

 no  
 

 ubi.com
 

 users
 

 password
 enteragain
 

 hdb
 

 yes
  no  
 no
 

 here  we need to enter the passwords  and desission 
 

 3 apt-get install apache2 smbldap-tools
 

 4 apt-get install phpldapadmin  
 

 

 

 crate file backend.ldif  and paste the following and rename your password  
 

 
> 

   
# Load dynamic backend modules dn: cn=module,cn=config objectClass: olcModuleList cn: module olcModulepath: /usr/lib/ldap olcModuleload: back_hdb.la  # Database settings dn: olcDatabase=hdb,cn=config objectClass: olcDatabaseConfig objectClass: olcHdbConfig olcDatabase: {1}hdb olcSuffix: dc=example,dc=com olcDbDirectory: /var/lib/ldap olcRootDN: cn=admin,dc=example,dc=com olcRootPW: secret olcDbConfig: set_cachesize 0 2097152 0 olcDbConfig: set_lk_max_objects 1500 olcDbConfig: set_lk_max_locks 1500 olcDbConfig: set_lk_max_lockers 1500 olcDbIndex: objectClass eq olcLastMod: TRUE olcDbCheckpoint: 512 30 olcAccess: to attrs=userPassword by dn="cn=admin,dc=example,dc=com" write by anonymous auth by self write by * none olcAccess: to attrs=shadowLastChange by self write by * read olcAccess: to dn.base="" by * read olcAccess: to * by dn="cn=admin,dc=example,dc=com" write by * read 


 

 

 

 crate file frontend.ldif  and paste the following and rename your password  
 

 

 

 
[CODE]
   
# Create top-level object in domain dn: dc=example,dc=com objectClass: top objectClass: dcObject objectclass: organization o: Example Organization dc: Example description: LDAP Example   # Admin user. dn: cn=admin,dc=example,dc=com objectClass: simpleSecurityObject objectClass: organizationalRole cn: admin description: LDAP administrator userPassword: secret  dn: ou=people,dc=example,dc=com objectClass: organizationalUnit ou: people  dn: ou=groups,dc=example,dc=com objectClass: organizationalUnit ou: groups  dn: uid=john,ou=people,dc=example,dc=com objectClass: inetOrgPerson objectClass: posixAccount objectClass: shadowAccount uid: john sn: Doe givenName: John cn: John Doe displayName: John Doe uidNumber: 1000 gidNumber: 10000 userPassword: password gecos: John Doe loginShell: /bin/bash homeDirectory: /home/john shadowExpire: -1 shadowFlag: 0 shadowWarning: 7 shadowMin: 8 shadowMax: 999999 shadowLastChange: 10877 mail: john.doe@example.com postalCode: 31000 l: Toulouse o: Example mobile: +33 (0)6 xx xx xx xx homePhone: +33 (0)5 xx xx xx xx title: System Administrator postalAddress:  initials: JD  dn: cn=example,ou=groups,dc=example,dc=com objectClass: posixGroup cn: example gidNumber: 10000

```

 sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.ldif
 
**sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.ldif** 

 

 

 

 now you can login to page using credential to the ldap  
 

 

 and download the file  
 

 [COLOR=#000080]_[http://sourceforge.net/projects/ldaputils/files/Conrib/mkntpwd.tar.gz/download?use_mirror=hivelocity](http://sourceforge.net/projects/ldaputils/files/Conrib/mkntpwd.tar.gz/download?use_mirror=hivelocity)_[/COLOR]
 

 

 extract it and copy the 7 file with out  
   
 in terminal go the directory were the file extracted and  
 

 

 make command  
 

 

 copy the mkntpwd to /usr/local/bin
 

 

 apt-get install samba samba-doc
 

 

 

 

 

 cd /usr/share/doc/samba-doc/examples/LDAP
 gunzip samba.schema.gz
 cp samba.schema /etc/ldap/schema
 

 

 

 First, create a conversion schema_convert.conf file containing the following lines:  
 
> 
   
include /etc/ldap/schema/core.schema include /etc/ldap/schema/collective.schema include /etc/ldap/schema/corba.schema include /etc/ldap/schema/cosine.schema include /etc/ldap/schema/duaconf.schema include /etc/ldap/schema/dyngroup.schema include /etc/ldap/schema/inetorgperson.schema include /etc/ldap/schema/java.schema include /etc/ldap/schema/misc.schema include /etc/ldap/schema/nis.schema include /etc/ldap/schema/openldap.schema include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema

 Next, create a temporary directory to hold the output:  
 
**mkdir /tmp/ldif_output** slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/cn=samba.ldif
   
 sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cn=samba.ldif
 

 

 

 Now you can sea that samba is enabled on the webpage  
 

 then need to install  this too
 

 apt-get install samba samba-client smbfs smbclient

[/CODE]

[https://help.ubuntu.com/10.04/serverguide/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/samba-ldap.html)

this link give me the code with out typing from watching the video .....

I am bigner in ldap configuration that may be the problem persist for me . I need configuration help form well know knowledge person  in ldap configuration . If you can ,please Rectify the above code and the video that i notified here I expecting all yours  effort for me to learn this topic .dont hesitate to replay I lost 20 day for this topic that y i asking to you all ...

---

### Post by Rakeshvijayan on 2013-04-19
any body have successes tutorial about the ldap with samba ?

---

