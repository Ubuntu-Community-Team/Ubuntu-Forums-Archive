---
title: "Apache2 change DocumentRoot"
date: 2017-09-13
forum: General Help
---

### Post by andrew772 on 2017-09-13
Hello. I have recently installed apache2 but I want to move the document root to another location, ideally keeping settings in their original location.

I have read the manual and searched the web and found I should open /etc/apache2/apache2.conf and change <Directory /var/www/> to the new location and also open /etc/apache2/sites-available/000-default.conf and change DocumentRoot to the same new location.

I have made both these changes and restarted the server but I'm getting 403 Forbidden when I try to access the webpage. It worked fine with the original settings. Is there something else I need to change somewhere? I also noticed the original location has the user:group settings of root:root, is this correct?

Thanks.

---

### Post by Habitual on 2017-09-13
There are few reasons to edit /etc/apache2/apache2.conf, IMO.

---

### Post by SeijiSensei on 2017-09-13
Any directory where the web site is stored must be readable by the www-data user.  This is likely a permissions problem.

I have all the websites I host stored in a specific user's home directory.  All the files in those directories are owned by that user and that user's group.  The web server "user," www-data on Ubuntu, is a member of that group and can read everything.

---

