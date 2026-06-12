---
title: "sendmail Permissions on 12.04.1"
date: 2013-02-10
forum: General Help
---

### Post by evanstimk on 2013-02-10
Realize this is swimming upstream, given that postfix is the default MTA  nowadays, but I have a complex sendmail config I need to recreate from  an old RedHat system. 

There seem to be permissions issues--the sendmailconfig program  (when executing /etc/mail/Makefile) can't write the access db to /etc/mail  (it can and does write other files there, including a new sendmail.cf).  Similarly,  /var/spool/mqueue can't be written to by sendmail either. 

Anyone know of this, and how to address it?

---

### Post by hash4all on 2013-03-22
/cd var/spool/
chown -R root:root mqueue
chmod g+w mqueue
cd /etc
chown -R root:root mail

try with above and test it again

---

