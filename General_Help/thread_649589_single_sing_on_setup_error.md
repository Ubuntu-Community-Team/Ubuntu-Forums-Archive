---
title: "single sing on setup error"
date: 2007-12-25
forum: General Help
---

### Post by Hotel on 2007-12-25
hi
i have been attempting to follow the single sing on tutorial  in the ubuntu community docs but when i attempt to install krb i get the following  error 
: Setting up krb5-admin-server (1.4.4-5ubuntu3.3) ...
kadmind: Improper format of Kerberos configuration file while initializing context, aborting

also the cofig screen dosn`t appear but a message telling me how to configure it but when i do what it says in the msg i get a similar error

is ther any way 2 fix this

---

### Post by Hotel on 2007-12-25
plz help!

---

### Post by kfries6 on 2008-01-08
I am seeing the same exact error.  In addition I saw a posting that indicated that it could be a DNS issue.  But my dnsdomainname command and realm only differ in case.

Does anyone out there have any idea what could be going on?  Absolutely no help in syslog either.

OS: Ubuntu Jeos 7.10
Ram: 128MB
Disk: 4GB

This is one of the first things I tried to install, so its still a pretty clean install.

Also asking desperately for help!!!

---

### Post by whit on 2008-02-13
You can get beyond that message by simply removing (or moving) the krb5.conf file. Not that I have this fully working yet ... but with modern versions of Kerberos that file isn't needed (or at least so the Samba docs say).

---

