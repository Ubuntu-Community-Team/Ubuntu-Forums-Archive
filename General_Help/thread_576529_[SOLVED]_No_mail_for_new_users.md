---
title: "[SOLVED] No mail for new users"
date: 2007-10-15
forum: General Help
---

### Post by btaylor101 on 2007-10-15
I am trying to add a new user via the command line (adduser) and it allows me to create the user, but a mail folder is not created. When I check the directory for the other user it has the mail folder. I am able to log into squirrel mail as the existing user, but the second user cannot log in. How do I create a user that automatically has a mail profile?

---

### Post by btaylor101 on 2007-10-15
Here is the error from my logs
Oct 15 08:58:29 BigBoss dovecot: IMAP(btaylor101): mbox: Can't create root mail directory /home/btaylor101/mail: Permission denied
Oct 15 08:58:29 BigBoss dovecot: IMAP(btaylor101): MAIL environment missing and autodetection failed (home /home/btaylor101)
Oct 15 08:58:29 BigBoss dovecot: child 8361 (imap) returned error 89

---

### Post by btaylor101 on 2007-10-15
I think this has something to do with auto discovery. I sent myself a test email and then I was able to log into squirrelmail and check the email. I was also able to see the mail folder in the home directory. I looked through the /etc/dovecot/dovecot.conf file under the heading **Mailbox locations and namespaces**to find out more.

---

