---
title: "configure apache/php for mysql"
date: 2007-10-11
forum: General Help
---

### Post by Guardian-Mage on 2007-10-11
I installed Apache,php, and mysql. Apache and PHP works fine, but when I use mysql_connect() in comes up with the error that the function doesn't exist. In windows I had to configure it, but I don't know where the files are in linux nor what to add to them. 

Also, how do I change the mysql database location so it points to a different location, in windows it was mysql.ini or something.

Thanks

---

### Post by Doo Doo on 2007-10-11
well did you install php5-mysql ?

---

### Post by the_nite_owl on 2007-10-11
Guardian-Mage, I have the same issue.

It's not a matter of installing PHP, the message itself shows that PHP is working.  It is the MySQL client libraries that have to be setup.

I have a LAMP install so PHP and MySQL were pre-installed.  The mysql.so line in my php.ini file is uncommented so it SHOULD be enabled.  I assume the library needs to be downloaded but I have not been able to find an up to date site with info on setting this up.

Anyone?
Not to hijack Guardian-Mage's thread, just providing some clarity on the problem and his solution should fix my problem as well.

Thanks.
Nite

---

### Post by the_nite_owl on 2007-10-11
Guardian-Mage, I seem to have fixed my problem.  I now have problems with the account my PHP page uses to connect but that's a different thread.  :)

The typical solution is to modify your /etc/php5/apache2/php.ini  file and uncomment the line for extension=msql.so

You can do this from a terminal window with the command:
sudo gedit /etc/php5/apache2/php.ini

Remove the semi-colon from in front of the line, save the file then stop and restart your database and apache.

If that does not work for you as it did not for me, I just went into Synaptic Package Manager and installed php5-mysql  that is the MySQL module for PHP5.  Once I did that (and restarted the db and web servers) it worked.

---

