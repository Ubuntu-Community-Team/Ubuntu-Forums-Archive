---
title: "Change path Maildir using Postfix/Dovecot"
date: 2018-06-28
forum: General Help
---

### Post by quvat77 on 2018-06-28
Hi!
I'm using Ubuntu 16.04. 
At this moment I have configured and working Postfix+Dovecot.
I'm using Maildir as mailbox.
Postfix:
/etc/postfix/main.cf
home_mailbox = Maildir/

Dovecot:
/etc/dovecot/conf.d/10-mail.conf
mail_location = maildir:~/Maildir


With this configuration the emails is stored on /home/user/Maildir.
But I'm looking to change this to a different drive from system. Ex:/media/data/Mail/user/Maildir.

Anyone can help me to solve this?
I've tryed a different ways like editting postfix file with: virtual_mailbox_maps + path.
But it did not works.

Any help will be apreciate.

---

### Post by btindie on 2018-06-29
Took a minute to google "postfix change maildir location" and find

> 
The easiest way is to set the mail_spool_directory to the new directory:


sudo postconf mail_spool_directory=/Location/Mail/
For this to work, home_mailbox must be empty:


sudo postconf home_mailbox=


assuming that's what you want to do? - move the local users maildir to a location other than their home directory.

Would also be worth a read depending on what you're trying to achieve:
[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html)
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

