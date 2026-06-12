---
title: "apache warning"
date: 2008-06-26
forum: General Help
---

### Post by SpikeyMike on 2008-06-26
Hello, I recently installed a LAMP stack on hardy and am trying to get it working properly, one problem I have is when I restart apache I get the following warning, can anyone advise me about this?

Spikey
[COLOR="Red"][I]

 * Restarting web server apache2                                                [Thu Jun 26 19:48:02 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/I][/COLOR]

---

### Post by pytheas22 on 2008-06-26
The "Could not reliably determine the server's fully qualified domain name" stuff is normal and I think happens whenever you don't have a hostname setup for your machine.

As for the other line, did you look at line 3 of /etc/phpmyadmin/apache.conf?

What else is going wrong that's preventing the server from working?

---

### Post by suicidejack on 2008-06-26
i installed lamp too on HH and i get the same error.  i'm not relaly sure what it is since I looked at my apache.conf file and couldn't figure out what it was talking about.  apache and everything runs fine so i have just been ignoring that message.

---

### Post by SpikeyMike on 2008-07-07
> **pytheas22 said:**
> The "Could not reliably determine the server's fully qualified domain name" stuff is normal and I think happens whenever you don't have a hostname setup for your machine.

As for the other line, did you look at line 3 of /etc/phpmyadmin/apache.conf?

What else is going wrong that's preventing the server from working?

hi, thanks for your reply, the webserver seems to be working ok although I am only using it locally at the moment, I cheched line 3 of /etc/phpmyadmin/apache.conf and this is what is there:

*Alias /phpmyadmin /usr/share/phpmyadmin*

not sure if this is what is causing the warning message, any ideas?

Spikey

---

### Post by pytheas22 on 2008-07-07
If everything is working alright locally, then it probably will be fine on the Internet as well.

Line 3 of /etc/phpmyadmin/apache.conf doesn't look like it should cause any problems.  I think it's normal to be like that...it's just specifying the full path to phpmyadmin.

---

### Post by comandrei on 2008-07-07
Add 
```

ServerName localhost

```
in /etc/apache2/httpd.conf

---

