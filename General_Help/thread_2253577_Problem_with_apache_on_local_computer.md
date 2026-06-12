---
title: "Problem with apache on local computer"
date: 2014-11-20
forum: General Help
---

### Post by kip2 on 2014-11-20
Hello.  
I installed Linux ubuntu 14.10 and have fixed everything EXCEPT the Apache section... 
Have installed it localy and everything is just a "joy to the hut" 
 
BUT, now I want to have the document root on my external hard drive and this is not easy ..  
 
I opened: /etc/apache2/sites-available/000-default.conf 
and changed it from : 
 
DocumentRoot /var/www/html 
to: 
DocumentRoot /media/kjelle/EC501EED501EBDF0 

Added these lines :

    <Directory /media/kjelle/EC501EED501EBDF0>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride none
        Order allow,deny
        allow from all
    </Directory>

saved and rebooted apache..

opened "/etc/apache2/apache2.conf" and added this:

    <Directory /media/kjelle/EC501EED501EBDF0>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride none
        Order allow,deny
        allow from all
    </Directory>
 Saved the file and restarted apache..

But then I get an error message when I open (in browser) localhost: 
 
"You do not have permission to access / on this server.....  "
 
Remember I struggled something awful with this last time I did a  complete reinstallation of ubuntu .. and then 10.04 .. Is there any real  gurus here that can please help me to fix this ??

---

### Post by yancek on 2014-11-20
The user:group for the partition on which you want the Document root should be www-data:www-data.  Is that the UUID of the partition you are using?  I would change that to something a little more logical or human-readable rather than a UUID but that's up to you.  If you are going to have the external drive attached all the time I would think it would be more practical to mount it under the /mnt directory and then put an entry in the /etc/fstab file for it to be mounted on boot.  If it's not going to be attached permanently then this would not be practical.

Check owner:group and permissions with:  ls -ld /media/kjelle/EC501EED501EBDF0

---

### Post by dragonfly41 on 2014-11-21
I've had the same error in the last few days when configuring apache2 virtualhosts.

First check what version of apache2 you have.

If apache 2.4 or greater take note that directives have **changed**.

[http://httpd.apache.org/docs/current/upgrading.html](http://httpd.apache.org/docs/current/upgrading.html)

It took me some time to spot this.

**Try this.**

Create a new virtualhost file in  /etc/apache2/sites-available/

e.g.  mysite.conf


In there have this code ... from the information you have provided

```

<VirtualHost *:80 >
  ServerName mymedia
  DocumentRoot /media/kjelle/EC501EED501EBDF0
  DirectoryIndex index.html index.php
  <Directory  "/media/kjelle/EC501EED501EBDF0">
    AddDefaultCharset UTF-8

    AllowOverride all
    Options +FollowSymLinks +Multiviews
    # note that '+' prefix is for apache 2.4+

    Order allow,deny
    Allow from all
    Require all granted
    # note that Require all granted is for apache 2.4+

    RewriteEngine on
    # you may have to add a rewrite rule
    
    </Directory>
  
    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel debug
    
</VirtualHost>

```

I've added optional LogLevel debug so you can inspect /var/log/apache2/error.log if this doesn't work out.

Now you must enable the virtualhost site ...
(I suggest that you first read up on defining virtualhosts in apache2).

sudo a2ensite mysite.conf

Then reload configuration (this allows you to change configuration without the need to restart apache).

sudo service apache2 reload

For good measure you can restart apache2 ...

sudo service apache2 restart

You can see a list of sites to enable or disable by running either

sudo a2ensite
or
sudo a2dissite

You can manually disable a site by deleting it from
/etc/apache2/sites-enabled/
and then using sudo a2ensite when you wish to place a site in that folder

You will have previously set ownership of /media/kjelle/EC501EED501EBDF0
to www-data:www-data.

After all this try accessing your virtualhost as ..

[http://mymedia](http://mymedia)

or whatever "server name" you have defined in your config file.


**Optional**

A useful tool to inspect virtualhosts and other configurations is webmin.

It is found in Ubuntu Software Centre.   But to use webmin you will need to enable SSL in apache2.
Another file is placed in /etc/apache2/sites-available/

You then access webmin via http**s**://localhost:10000/

---

### Post by dragonfly41 on 2014-11-21
Sorry .. I left out one more step if you are running in localhost.

After all the editing of virtualhost files ... go to /etc/hosts

add a line for each of your virtualhosts (based on servername)

e.g.

```

127.0.0.1    localhost
127.0.0.1    mymedia
# if you are using 'mymedia' as your servername

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

