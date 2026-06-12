---
title: "Question on Apache permissions"
date: 2007-08-15
forum: General Help
---

### Post by 5circles on 2007-08-15
After installing moinmoin and reviewing a bunch of questions on the forum, I have a question about the permissions for Apache.

/etc/init.d/apache2 was originally set as root.root.  MoinMoin worked OK.  Then I changed it to www-data.www-data consistent with some of the messages here, restarted, and MoinMoin still works.

What should the permissions be?  Why were mine set to root.root?  Could it be something to do with the way I installed Ubuntu Feisty Fawn in the first place (as a desktop, not LAMP)?

I'm also curious about why the apache restart shows the following message "could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName'   This is displayed twice.

Thanks

---

### Post by upthelum on 2007-08-15
I'm unsure about the permissions but "could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName' could mean Apache isn't running, try sudo apache2 graceful then apache2 restart.

---

### Post by 5circles on 2007-08-15
No Apache is running fine - sorry if I wasn't clear.  I suspect that I just have the network set up slightly wrong.  But I can access from other machines by name with no problem

---

### Post by az on 2007-08-15
The init.d scripts should be root.root.  That will not change the fact that apache runs as www-data.  Why did someone tell you to do that?

To get rid of the warning, you need to set your servername in the apache configuration.  You can ignore the warning.

---

### Post by 5circles on 2007-08-15
I changed the ownership of the /etc/init.d/apache2 file back to root.root - I see where the user and group is set in the conf file.  

Thanks for the clarification.  I'm not quite sure where I spotted the suggestion. I probably misinterpreted the message when trying to configure moinmoin, and then discovered that the problem I had was caused by misreading.  I was trying to make sure that everything was set up as correctly as possible.

---

