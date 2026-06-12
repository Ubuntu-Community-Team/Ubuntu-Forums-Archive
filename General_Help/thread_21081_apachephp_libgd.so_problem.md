---
title: "apache/php libgd.so problem"
date: 2005-03-20
forum: General Help
---

### Post by akshoslaa on 2005-03-20
I've been messing around the last couple of days starting to (finaly) learn php...
Some example code I've been playing with calls the gd library, so I checked synaptic, and both version 1 and two are installed.. all good...

However the code returned that gd couldn't be detected... dig around and notice 
that the gd extension isn't listed in phpinfo...

dig around some more, compile the latest version of the library from source, mess around with php.ini pointing it to various locations and filenames (libgd.so, .so.2, .so.2.0.23 etc etc etc) all to no avail...

Then I remembered the concept of log files (still new to Linux :P)

had a look in /var/log/apache2/error.log and found this:

PHP Warning:  Unknown(): Invalid library (maybe not a PHP library) 'libgd.so'  in Unknown on line 0

after each restart (with different filenames as tried above)
any idea what's going wrong?

(mysql.so in the same location loads fine)

---

### Post by kmslinux on 2007-10-31
Do you have the file libgd.so? If you do, please post the contents.

---

