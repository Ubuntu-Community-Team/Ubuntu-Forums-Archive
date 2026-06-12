---
title: "chmod with serious consequences"
date: 2008-05-08
forum: General Help
---

### Post by wups on 2008-05-08
Hi, I made this typo with serious consequences on my ubuntu 7.10 Server as user root
chmod 775 temp/ **/** -R

I have backups but not for system yet because the server is new. 

Now several services won't work 100%:

mysql: "unable to connect to database" when executing a php-file 
ssh: it's not possible to connect via ssh
postfix: unable to send mails


How can I restore permissions?

---

### Post by Yannick Le Saint kyncani on 2008-05-08
AFAIK, you can't.

So get the list of installed/wanted packages with either debfoster, deborphan or dpkg --get-selections and reinstall everything.

---

### Post by cmcanulty on 2010-08-15
I installed debfoster but can't figure out how to run it. Double clicking the executable didn't do anything.

---

### Post by oldos2er on 2010-08-15
debfoster is a CLI program, so it needs to be run in a terminal.

---

