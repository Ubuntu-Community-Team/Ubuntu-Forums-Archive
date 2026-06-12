---
title: "My Syslog shows something is trying to use my email server"
date: 2014-03-22
forum: General Help
---

### Post by cje1232 on 2014-03-22
Hi
These two lines comes up every minute in my syslog:
> Mar 22 21:29:01 www CRON[3214]: (root) CMD (cd /var/www2/domain/site/periodic; /usr/bin/php -q cron.php)
Mar 22 21:29:01 www CRON[3213]: (CRON) info (No MTA installed, discarding output)

Seems like there are some sort of script trying to access an old website folder, which doesn't exist anymore, to, maybe, send out emails/spam...
How may I figure out what it is, and what do I do next?

Thanks for any suggestions and help.

---

### Post by TheFu on 2014-03-22
According to the logs, those commands are being run from the crontab - so either a crontab entry needs to be cleaned up 
OR
you've been hacked.

---

### Post by cje1232 on 2014-03-22
TheFu, thanks for your feedback. I suppose both answers are true; there has been something installed on my system which are trying to execute a file which try to send out spam, but doesn't succeed due to the missing mail server.

Any suggestions how I can clean it up?

---

### Post by TheFu on 2014-03-22
I would restore from a backup prior to the log messages beginning.
Then I'd look for how they could have gotten in to ensure it isn't still possible.
In the last few weeks, I helped someone else here running php webapps learn the risks they were taking. Search the forums.

Good backups are the #1 security tool.

---

### Post by cje1232 on 2014-03-23
Thanks for your suggestion. So, there are no other solutions to find and remove the script?
I suspect the hack was done through a wordpress ad on. Which has been removed. 
I don't know if it's physical or virtual, but what concerns me is the apparently use of the "root" user.

---

### Post by TheFu on 2014-03-23
Sure there are other solutions, it just isn't easy to describe them in a forum, since many different methods would be involved. Realistically, reinstallation would be what I did. A hacked OS can never really be trusted again.

PHP is a major security issue. So is java, IMHO.  Just read the OWASP references [https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)  about these languages.> 
There are, unfortunately, serious issues in all areas that make it difficult to write secure PHP applications. These are difficult to work around if you are forced to use PHP, but you need to be aware of them.

In short - don't use php if you have a choice. Where I work, we don't allow PHP on the internet.

---

