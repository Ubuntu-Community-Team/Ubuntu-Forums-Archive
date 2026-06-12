---
title: "phpmyadmin 403 error"
date: 2008-06-07
forum: General Help
---

### Post by hvshah69 on 2008-06-07
I installed phpmyadmin using apt-get command. However, the browser throws 403 Forbidden error when I try to access phpmyadmin

The package is installed in /usr/share folder and the permissions seem to be fine. 

I think that I need to change apache configuration file but not sure what exactly?

Can someone please help. Thanks.

---

### Post by fsmithred on 2008-06-08
Works ok for me in hardy. 

```
sudo apt-get install apache2 phpmyadmin
```

Then send your web browser to:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

If you did more than that, such as editing config files or changing permissions, then you need to give more details. BTW, I'm far from an expert with apache setups.

Is apache working ok? Did you get the "It Works!" page when you went to [http://localhost?](http://localhost?)   You can look in /var/log/apache2/error.log for error messages.

---

### Post by mbsullivan on 2008-07-01
Normally this is because your permissions aren't set such that you have read or execute access to the phpmyadmin files.

You could try chmod'ding the files as follows:

```
sudo chmod 755 [phpmyadmin files]
```

Mike

---

### Post by tombart on 2010-05-05
try to edit your /etc/apache2/conf.d/phpmyadmin.conf

and add there

```

order deny,allow
deny from all
allow from 127.0.0.1

```

inside block:
```

<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
</Directory>

```

or there could be also /etc/phpmyadmin/apache.conf file with same content, depends on apache.conf file which one is loaded

---

