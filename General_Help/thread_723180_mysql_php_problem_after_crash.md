---
title: "mysql php problem after crash"
date: 2008-03-13
forum: General Help
---

### Post by pylon42 on 2008-03-13
'ello,

I have php/mysql installed on my local machine for testing purposes. I'm very new to the server-side of things. I had everything up and running with no problems for about a day, but then I experienced a hard-lock. I rebooted and was presented with the following error when trying to view sites locally:

Fatal error: Call to undefined function mysql_connect()

I've reinstalled php5-myql but it doens't seem to have worked...

Any suggestions? Short of starting over from scratch?

---

### Post by OffAxis on 2008-03-13
Can you pull up a phpinfo page?
There's a section in there for mysql that'll tell you what version of the module you're running, and more importantly, if it IS running.

A phpinfo page is just a call to phpinfo (I'm not sure if you've come across it before so I'll elaborate).
Here's the text of it:

<?php
phpinfo()
?>

That's it. Save it as phpinfo.php, put it on your web server, and navigate there.

---

### Post by pylon42 on 2008-03-13
Thanks for your response. According to the phpinfo() page, the only reference to "mysql" is the following:

additional .ini files parsed:
/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini

Is there something else I should be looking for?

---

### Post by OffAxis on 2008-03-13
There should be something that looks like the attachement below.

If the module isn't registering for some reason you'll need to modify the configuration file and makes sure the correct path to the module is present.


HOWEVER, probably the easiest way of dealing with this is just installing phpmyadmin

```
sudo apt-get install phpmyadmin
```

which will install and register the necessary dependencies (which is php5 with the mysql modules)

Otherwise, you can search your packages with something like

```
sudo aptitude search php
```

and look for what's **i** (installed) versus what's **a** (available) and not installed.
Once that's verified, tackle those config files that you listed and make sure everything is uncommented and pathed correctly.

Note: To actually use phpmyadmin you'll need an appropriate link in there (from your web server folder) to the newly installed phpmyadmin folder. Something like
```

cd /webserver/root
sudo ln -s phpmyadmin /usr/share/phpmyadmin/
```

Then use your browser to go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by pylon42 on 2008-03-13
Thanks for the screenshot - I definitely don't have a mysql reference in the phpinfo()

If I were to assume my php.ini file was corrupt, how would I go about getting a fresh copy?

I've renamed it, then removed and installed every service I could think of but none seem to be creating a new copy of php.ini... or maybe that's the wrong approach...

I've also installed phpmyadmin...

Is there a sample php.ini somewhere that I could look at/grab?

---

### Post by pylon42 on 2008-03-13
I found a reference that says:

```
;extension=mysql.so
```

needs to be uncommented in php.ini, but that line doesn't exist in mine.

Now I'm really confused...

---

### Post by OffAxis on 2008-03-13
I don't have that line in mine either; and mine works.
I've attached a copy for ya.

Edit: Or not.

Sorry- it was too big; had to zip it.

---

### Post by OffAxis on 2008-03-13
Alright, so someone's been mucking about with the configuration files on the structure & packaging side of things.

The actual spot for enabling mysql is now in the 
**/etc/php5/conf.d/mysql.ini** file, and here's what the contents should be:

```

# configuration for php MySQL module
extension=mysql.so
```

---

### Post by pylon42 on 2008-03-13
Your copy of php.ini worked perfectly - I must have had a stray character in there or something... who knows - I'm just glad to be back up and running :)

Thanks so much for your help!

---

### Post by OffAxis on 2008-03-13
you're welcome.

---

