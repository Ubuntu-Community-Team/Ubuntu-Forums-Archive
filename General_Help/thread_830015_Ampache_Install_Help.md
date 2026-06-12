---
title: "Ampache Install Help"
date: 2008-06-15
forum: General Help
---

### Post by b0ng0 on 2008-06-15
I have added ampache to the repos and installed everything that was mentioned on the website guide (e.g. myphp, sql, ampache, etc.).

However, when I go to [http://localhost/ampache/](http://localhost/ampache/) to finish the install I get this message:

> Warning: require_once(lib/class/database_object.class.php) [function.require-once]: failed to open stream: No such file or directory in /usr/share/ampache/www/install.php on line 28

Fatal error: require_once() [function.require]: Failed opening required 'lib/class/database_object.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/ampache/www/install.php on line 28

I have made sure that the php conf file is in /etc/apache2/conf.d/ as I read in another post, but I have no idea what would be wrong. 

Thank you for any help :)

---

### Post by pytheas22 on 2008-06-15
Take a look at the file /usr/share/ampache/www/install.php and see what it's trying to open on line 28.  I'm not familiar with ampache, but just going by the error message, it looks like the application thinks that the file it's try to open doesn't exist.

---

