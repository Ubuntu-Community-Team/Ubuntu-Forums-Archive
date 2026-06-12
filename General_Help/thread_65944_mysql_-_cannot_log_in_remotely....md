---
title: "mysql - cannot log in remotely..."
date: 2005-09-15
forum: General Help
---

### Post by sergio_101 on 2005-09-15
okay, i have been working on this for two full days, and i am just missing something..

i have a new intallation of ubuntu going.. this is my first ubuntu, but i have been using slackware/redhat/fc since the very beginning..

my problem is, i need to have a client able to log into the mysql server from his site..

i searched all over this forum, and found some great info, but there is just one more piece i am missing..

i commented out the "skip-networking"  part.. and that opened up port 3306..

i added a user "root" with full priveledges from anyhwere.. i know this is a bad idea, and i will change that as soon is i can get a login..

i can login from the command line using:

mysql -u root -p

and that logs me in..

but when i try to log in from outside..

no dice..

oh.. the host entry for "root" is: %

anyone have any ideas?

thanks in advance!

---

### Post by sergio_101 on 2005-09-15
one more thing..

if i login from another machine at the command line, here's what i get:

```
[sergio@poopakunga webmin]$ mysql -h xxx.xxx.xxx.xxx-u root -p
Enter password: 
ERROR 1045: Access denied for user: 'root@acs-xxx-xxx-xxx-xxx.zoominternet.net' (Using password: YES)
```

---

