---
title: "How do I enable .htaccess in apache 2?"
date: 2006-08-25
forum: General Help
---

### Post by simon360 on 2006-08-25
I have googled for it everywhere, but I can't figure it out. .htaccess file don't work on my server, and I want to know how to enable them. I think it's a line somewhere in apache2.conf, but I'm not sure where. I haven't changed my apache2.conf at all, and I don't have any mods installed.

I'm using Ubuntu 6.06 LTS.

---

### Post by audax321 on 2006-08-25
I found this documentation on the Apache site:

[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

It says to put the following line if the server config if you want to use a name different that .htaccess:

AccessFileName .<whatever_you_want>

If the .htaccess files aren't working for you by default, try adding:

AccessFileName .htaccess

Also, you might need to setup some of the other options indicated on that page as well in the configuration file. I haven't dealt with .htaccess files in Apache too much, but I hope this helps.

---

### Post by Sam on 2006-08-25
Don't forget the [AllowOverride](http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride) directive, too.

---

### Post by simon360 on 2006-08-25
Thanks guys. You'll never get in! Muahahahahaha! :P

---

### Post by Arjunanda on 2006-10-12
The conf file in apache2 is completely different from apache1 versions. The structure is different and there are less explanatory comments. I do not find similar .htaccess section in apache2 config like in apache1.

Should these be entered between the <Directory /var/www> </Directory> tags? What is the right section?

---

### Post by gokusandwich on 2006-10-21
I've created a wiki page for this issue: [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

---

