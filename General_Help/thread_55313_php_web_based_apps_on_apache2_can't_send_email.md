---
title: "php web based apps on apache2 can't send email"
date: 2005-08-08
forum: General Help
---

### Post by EricBaenen on 2005-08-08
I'm having trouble with an Ubuntu server install - this is actually less of an Ubuntu issue than a apache2/php4/mysql4/postfix issue - but I haven't found any help in any other non-Ubuntu forum so I thought I would ask here.

My install... Ubuntu 5.04...
- apache2
- php4
- mysql 4.0
- bind9
- postfix
- courier imap

all installed from standard packages - nothing custom compiled...

under apache2 I have a php based groupware app installed called TikiWiki ([www.tikiwiki.org](www.tikiwiki.org)) and phpwiki ([www.phpwiki.org](www.phpwiki.org))

Everything is working perfectly - except the php apps won't send email (for various notifications).  I've configured /etc/php4/apache2/php.ini so that for mail it points to /usr/sbin/sendmail - the postfix sendmail compatibility executable and I think I have all the right php and apache2 modules installed - but the apps just won't send email.

Any suggestions?

Thanks,

Eric

---

### Post by dave9191 on 2005-08-08
You want to configure postfix to send mail with proper details. I've not done this yet on my computer, but when I send mail from php it comes from [email]www-data@localhost.loca[/email]ldomain which would normally be rejected by mail servers. You need to put a valid email address on there. In sendmail this is called masquerading. I haven't messed around with postfix tho. 

So look at configuring postfix, Im sure that there are guides online. And maybe the config file is easy enough. 

Dave

---

