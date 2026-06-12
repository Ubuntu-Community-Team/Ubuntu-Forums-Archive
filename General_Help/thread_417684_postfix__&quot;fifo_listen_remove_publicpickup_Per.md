---
title: "postfix  &quot;fifo_listen: remove public/pickup: Permission denied&quot;"
date: 2007-04-21
forum: General Help
---

### Post by gneville on 2007-04-21
Hi All,

Im currently going through a very helpful tutorial on how to set up a mail server found here:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I have gone through every set and all of it is okay expect the Postfix program!

I used apt-get to install postfix and follwed the questions it asked, e.g. FQDN e.t.c.

I was getting these errors below,but then found out that "postfix" user wasnt added into the "postfix" group, so did **"useradd postfix -g postfix"**

**gneville@nocserver:~$ sudo /etc/init.d/postfix start**

** * Starting Postfix Mail Transport Agent postfix                                                                                                             postfix: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix                              [fail]**

**gneville@nocserver:~$ postalias /etc/postfix/aliases**
**postalias: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix**


Post Fix now starts and say [ ok ], however when I do a "**netstat -tnp**" its not listening on port 25, and I can't telnet into it.

If i tail the log file I can see this error message appears when ever I try to start postfix:

**Apr 22 01:43:52 nocserver postfix/master[8221]: fatal: fifo_listen: remove public/pickup: Permission denied**

I read a post saying its because of the permissions of main.cf / master.cf e.t.c, however I have tried all permission rights and nothing changes.

Please Help!

Thanks in advance.

Graham

---

