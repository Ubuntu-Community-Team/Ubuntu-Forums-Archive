---
title: "ldap authentication against a gentoo server"
date: 2007-03-29
forum: General Help
---

### Post by slaterson on 2007-03-29
hi,
i am new to ubuntu, i just downloaded the cd and installed it on a desktop machine a couple days ago.  so far i like ubuntu and i'd like to start using it, however i have one last obstacle to overcome that i can't seem to figure out: authenticating logins against my secure openldap server (a gentoo box - here is a link to the guide that was used to setup the ldap server: [http://gentoo-wiki.com/HOWTO_LDAPv3)](http://gentoo-wiki.com/HOWTO_LDAPv3)).

i have authenticated against this server with a gentoo linux client without problems, so i am confident it is working properly.

here is what i have done so far:
1) installed ubuntu
2) installed the ldap, libnss-ldap and libpam-ldap packages
3) manually edited the conf files so point to my server (for some reason they were not updated even though i entered the info during install of the packages in step 2).

when i run ldapsearch i get an error saying the server can't be reached and bad certificates.  and when running ldapsearch with debug output it mentions that the certificate is self-signed (which it is) and is bad.  this doesn't make a lot of sense to me as this exact server setup has worked with other clients (non-ubuntu).

can anyone help?  i'm stumped and would really like to get this working.

thanks,
slate

---

### Post by slaterson on 2007-03-30
nobody uses ldap?

---

### Post by firehead_eom on 2007-07-11
Hi, 

I know how frustrating it is to get LDAP authentication. 
I was in the same situation as you, and followed [this guide]("http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2") . 
[URL="http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2"]
http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2[/URL]

It's page 2 of the tutorial, which will allow you to point your terminals to the server for authentication. 

First, I activated Universe and Multiverse on Ubuntu, then updated everything. 
When inputting the LDAP server, I used the server's IP, to keep things simple and straightforward.

---

