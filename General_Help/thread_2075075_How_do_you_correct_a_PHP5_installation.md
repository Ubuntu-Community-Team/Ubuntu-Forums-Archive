---
title: "How do you correct a PHP5 installation?"
date: 2012-10-22
forum: General Help
---

### Post by Randy Schilling on 2012-10-22
I'm trying to include PhpMyAdmin in my LAMP installation.

I've have two <VirtualHost> sections working under 
name-based virtual hosting:

<VirtualHost *:80>
    ServerName     localhost:80
    ServerAdmin    <removed email>
    DocumentRoot   /usr/local/apache2/htdocs/default/
     DirectoryIndex index.html
     ErrorLog       logs/default/error_log
     TransferLog    logs/default/access_log
</VirtualHost>

<VirtualHost *:80>
    ServerName     [http://rjs357.com:80](http://rjs357.com:80)
    ServerAdmin    [email]<removed email>[/email]
    DocumentRoot   /usr/local/apache2/htdocs/rjs357/
     DirectoryIndex index.html
     ErrorLog       logs/rjs357/error_log
     TransferLog    logs/rjs357/access_log
</VirtualHost>

I've used a src-based installation for Apache and PHP 
and I've done the same for PhpMyAdmin.  I downloaded
a tar.gz file, unzipped and detarred it, creating a directory
/usr/local/apache2/htdocs/phpMyAdmin-3.5.3-english/.
This directory contains  an index.html and many .php
files.

Its not clear to me from the documentation,
[www.phpmyadmin.net/documentation/#quick_install](www.phpmyadmin.net/documentation/#quick_install),
how to access PhpMyAdmin from my web browser.
I think this information would be in the link
in step 6 of the instructions, but that link is a dead end.

Have I installed PhpMyAdmin to the correct directory?
Do I need to change my default, the first, <VirtualHost> block?
Do I need to create a third <VirtualHost> block?
Where and with what directives?


Thanks and grateful to have this forum for help, Randy

---

### Post by Randy Schilling on 2012-10-23
I used a source-based installation of php5.
My ./configure command had a certain set of --with options.
Now I want to install phpMyAdmin and according to my reference,
[http://www.thegeekstuff.com/2010/09/install-phpmyadmin/](http://www.thegeekstuff.com/2010/09/install-phpmyadmin/),
I should have used a different set of options in my PHP ./configure command.
Can this be corrected without doing an uninstall followed by a reainstall?

Thanks and fortunate to have this forum for help, Randy

---

### Post by pqwoerituytrueiwoq on 2012-10-23
once you install [phpmyadmin](apt:phpmyadmin) go to [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

---

### Post by ~LoKe on 2012-10-23
How about...
```
sudo apt-get install phpmyadmin
```

---

### Post by Randy Schilling on 2012-10-23
The problem is one of installing phpMYAdmin. I can't use it yet.

The package-based install (using apt-get) sets things up in a certain way,
which doesn't work with my source-based installation.

---

### Post by ~LoKe on 2012-10-23
> **Randy Schilling said:**
> The problem is one of installing phpMYAdmin. I can't use it yet.

The package-based install (using apt-get) sets things up in a certain way,
which doesn't work with my source-based installation.

I'm not sure why you're trying to install from source.

---

### Post by nothingspecial on 2012-10-23
Merged.

---

### Post by Randy Schilling on 2012-10-23
~LoKe: because I found more documentation concerning the source-based install,
well, besides that, I'd never worked before with sources and  I'm curious.

---

### Post by ~LoKe on 2012-10-23
Out of curiosity, could you put a file named "info.php" into /var/www/ with this in it:
> 
<?php
phpinfo();
?>
Then navigate to it (127.0.0.1/info.php) and give me the output?

---

### Post by Randy Schilling on 2012-10-23
LoKi: Yes, I have <?php phpinfo();?> working out of two <VirtualHost>...</VirtualHost>
blocks.  See the first post of this thread.   

You can check out one of them at [http://rjs357.com/](http://rjs357.com/).

---

### Post by ~LoKe on 2012-10-23
[http://www.thegeekstuff.com/2010/09/install-phpmyadmin/](http://www.thegeekstuff.com/2010/09/install-phpmyadmin/)

---

### Post by Randy Schilling on 2012-10-23
Go to [http://rjs357.com/](http://rjs357.com/), click the link, and look at the third row of the first table.
"Configure command" shows the options I used to install php5.

My reference for a src-based installation of phpMyAdmin is 
[http://www.thegeekstuff.com/2010/09/install-phpmyadmin/](http://www.thegeekstuff.com/2010/09/install-phpmyadmin/).
In step I I'm told I should have used the following configure command:
./configure --with-apxs2=/usr/local/apache2/bin/apxs /
--with-mysql --with-bz2 --with-zlib --enable-zip     /
--enable-mbstring --with-mcrypt

What I want to do is to update my php5 configuration to include these additonal features.  Once done, I  can complete the phpMyAdmin installation.
I'd very much like to avoid uninstalling and then reinstalling php5.
I'm reading through the php5 documentation but I wish 
someone like you would just tell me what to do.

---

### Post by Randy Schilling on 2012-10-23
The reference you'd expect to work,
[http://www.phpmyadmin.net/documentation/](http://www.phpmyadmin.net/documentation/),
fails because the link in its step 6 is a dead end.
I don't think it would work anyway.

---

### Post by ~LoKe on 2012-10-23
Just go back to the php5 source directory and run the command over again
```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-bz2 --with-zlib --enable-zip --enable-mbstring --with-mcrypt
```

---

### Post by Randy Schilling on 2012-10-23
The reference
[http://www.php.net/manual/en/install.unix.apache2.php](http://www.php.net/manual/en/install.unix.apache2.php)
tells us what to do to change options:


"If you decide to change your configure options after installation,     you'll need to re-run the configure, make, and make install steps.      You only need to     restart apache for the new module to take effect. A recompile of     Apache is not needed."

---

### Post by ~LoKe on 2012-10-23
Yep, refer to my post above.
```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-bz2 --with-zlib --enable-zip --enable-mbstring --with-mcrypt
```
After that goes though, run...
```
sudo make;
sudo make install
```

---

### Post by Randy Schilling on 2012-10-23
Bottom line best references for source-based installations:
apache2 and php5:   [http://dan.drydog.com/apache2php.html](http://dan.drydog.com/apache2php.html)
phpMyAdmin              [http://www.thegeekstuff.com/2010/09/install-phpmyadmin/](http://www.thegeekstuff.com/2010/09/install-phpmyadmin/)

To update a php installation,  repeat all the steps in dan.drydog's reference,
# ./configure..., (with appropriate options)
#make 
#make install 
the cp statments and so on.

Thanks, grateful for all of your help, Randy.

---

