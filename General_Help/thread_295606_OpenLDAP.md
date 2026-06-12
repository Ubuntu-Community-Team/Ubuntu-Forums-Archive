---
title: "OpenLDAP"
date: 2006-11-08
forum: General Help
---

### Post by damvcoool on 2006-11-08
hello i was wondering if there is anyone that can tell me, or at least point to me, where can i find a good how-to install and configure OpenLDAP on Ubuntu.

NOTE: I was following a fedora installation and configuration of LDAP but the slapd.conf is very different on both distros.


I also need a good configuration example :D

Thank You!!

---

### Post by damvcoool on 2006-11-13
Someone Please Help me!! :P

---

### Post by Abhi Kalyan on 2006-11-14
> **damvcoool said:**
> Someone Please Help me!! :P
try installing the following
libldap2- preinstalled
libldap-2.2-7 - i installed
libldap2-dev -i installed
ldap-utils - i installed
slapd - i installed
above dependencies
libdb4.2
libiodbc2
libltdl3

later also install
php support for ldap
then install
phpldapadmin

I have come till this point and trying to go ahead.
Cheers All the best.
Sincerely
Abhi Kalyan

---

### Post by cyris| on 2006-11-14
no one has attempted this? i'll be needing to setup an ldap server shortly and i was hoping to do this on ubuntu.

---

### Post by Abhi Kalyan on 2006-11-14
try luma, its pretty convenient ,
one thing is the authentication part, trying to figure it out.
luma looks better than phpldapadmin.
Trying to source info
Cheers

---

### Post by damvcoool on 2006-11-15
I also found a good guide to start and a good gui that manages LDAP, the gui is called LAT(LDAP Administration Tool) and the guide is in this address

```
https://help.ubuntu.com/community/OpenLDAPServer
```


NOTE:
by the way, for those who are just starting with ldap(like me) if the an error comes saying that the syntax is invalid try using the cn=admin,dc=yourdomain, or whatever you used as the admin on the slapd.conf

NOTE2:
ubuntu should have some ldap project similar to fedora directory service, is very popular to have a Directory Services on the server side:D

---

### Post by Abhi Kalyan on 2006-11-15
thank you damvcoool,
Checking out the site.
i forgot to mark
db4.2-utils while installing install this too.

Having a problem with editing the slapd.conf,
dont know what has to go where.
will seek.
Thank you once again.
What do you think about luma?

---

### Post by Abhi Kalyan on 2006-11-15
"I also found a good guide to start and a good gui that manages LDAP, the gui is called LAT(LDAP Administration Tool) and the guide is in this address"

Where did you find the tool, couldnt get it on the synaptic?
could you please point.

---

### Post by Abhi Kalyan on 2006-11-17
Done at last 
Forgot to give an enter and a white space was stopping any type of authenticaion.
LDAP Work and Works Beautifully
Thank you UBUNTU thank you Linux, Thank you all
Cheers!!

---

### Post by cyris| on 2006-11-20
Glad everything worked out for you :D

I followed the following article and it got me up and running with a basic ldap setup in 30mins.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

