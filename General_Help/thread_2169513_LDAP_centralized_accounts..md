---
title: "LDAP centralized accounts."
date: 2013-08-22
forum: General Help
---

### Post by rahuljanghel on 2013-08-22
Hi All,

My requirement is as below :

I have 10 servers on cloud, all server with a public IP. right now we are ssh/putty to all server with created account on all those server individually.
I am asked to deploy a LDAP server which will hold all user account need to authenticate those server.

so, when I ssh any server using public ip, server will send that auth job to LDAP server, ldap will authenticate it and then user can loging to that server.

I tried many documents, blogs also from ubuntu site but unable to make it working.

pls help. incase require more clarity on requirement, pls let me know. i will elaborate more.

Regards,
Rahul Janghel.

---

### Post by newbie-user on 2013-08-23
You'll obviously need to set up an LDAP server. Then you would install libpam-ldap on your other servers and add the "ldap" setting to their nsswitch.conf files. That's basically it. Have you checked your log files to see what errors may be preventing you from authenticating via ldap?

---

### Post by rahuljanghel on 2013-09-10
I Used below URL to setup my server and client, and its working smoothly. 
[http://www.supportsages.com/blog/2012/06/ldap-configuration-for-user-and-group-centralization-on-ubuntu-12-04-lts-part-1/](http://www.supportsages.com/blog/2012/06/ldap-configuration-for-user-and-group-centralization-on-ubuntu-12-04-lts-part-1/)

Thanks a lot.

now facing difficulty difficulty making RHEL 6.4 client of that LDAP server.
Nothing in log file. 
Can any one suggest any doc or step for this.

Regards,
Rahul Janghel.

---

