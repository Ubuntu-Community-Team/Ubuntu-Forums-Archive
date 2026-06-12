---
title: "Apache 2 ignores configuration changes"
date: 2006-10-19
forum: General Help
---

### Post by mn_kthompson on 2006-10-19
I'm sorry if I'm posting this to the wrong area of the forums.

I'm running apache2 on my Dapper box, and it seems that when I make changes to the configuration file /etc/apache2/sites-available/default and then run /etc/init.d/apache2 reload (or restart) the server seems to ignore the changes that I made in that file.

Specifically, I had a line that read 
Alias /mediawiki /var/lib/mediawiki
I commented that line out and put in 
Alias /mediawiki /usr/share/mediawiki-1.8.2

I also added all the proper <Directory> statements.  However, when I try to access the directory I'm getting a 404 error.  According to /var/log/apache2/error.log it is still trying to access the file from /var/lib/mediawiki instead of /usr/share/mediawiki-1.8.2.  

Any thoughts?

---

### Post by mn_kthompson on 2006-10-19
Ahhh sneaky.  I found the problem.  When mediawiki was installed it created a file /etc/apache2/conf.d/mediawiki.conf and there was an alias in there that was conflicting with what I had put in the other file.

---

