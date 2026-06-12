---
title: "Option FollowSymLinks not allowed here after upgrade to apache 2.2"
date: 2007-09-01
forum: General Help
---

### Post by dyvel on 2007-09-01
Hi all
First post here :)

I hope you can help me with my problem. I simply can't figure it out.
After I opgraded from apache 2.0 to 2.2.3 my .htaccess file give me some trouble.

From my error log I get Option FollowSymLinks not allowed here

My question is, how can I "reallow" FollowSymLinks ???

Kind regards
Daniel

---

### Post by dyvel on 2007-09-01
my 000-default file looks like this:
NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                RedirectMatch ^/$ /d-form.dk/website/
        </Directory>


and my site file

<VirtualHost *:80>
        DocumentRoot /var/www/domain.info//website
        ServerName [www.domain.info](www.domain.info)
        ServerAlias domain.info
        ServerAdmin [email]webmaster@domain.info[/email]
        php_admin_value open_basedir /var/www/domain.info//website:/var/lib/php5
        ErrorLog /var/www/domain.info//logs/error.log
        CustomLog /var/www/domain.info//logs/access.log combined
        ServerSignature Off
</VirtualHost>

---

### Post by dyvel on 2007-09-01
anyone???
I'm going nuts here...

---

### Post by Nuggit on 2007-09-02
Haha, wow, I was having a similar problem and this topic came up when I googled it. I was about to say, "I want to know too" but I found the solution. :B

In your apache2.conf, you have to add
<Directory /pathto/whereveryouneed/symlinks/enabled>
AllowOverride All
</Directory>

and then, in the .htaccess of wherever you need symbolic links enabled, write
Options +FollowSymLinks

And then restart Apache.

I'm a total newbie at this, and I might be doing something wrong for all I know, but at least it works. For me.
I hope that helps.

---

### Post by dyvel on 2007-09-02
I have already tried that without any difference.

---

### Post by milwell on 2008-02-13
me too, i already have the directory 
allowoverride all 
command

but it's still not working

using ubuntu 7.10

```

<Directory /home/sysadmin/QA/web >
    AllowOverride All
    Allow from all
</Directory>


<Directory /home/sysadmin/QA >
    AllowOverride All
    Allow from all
</Directory>


<VirtualHost *>
        ServerAdmin webmaster@mail.ksk
        ServerName manufacturing.ksk
        DocumentRoot /home/sysadmin/symfony/QA/web
        ErrorLog /var/log/apache2/error-manufacturing.ksk.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel debug
        CustomLog /var/log/apache2/manufacturing.ksk.log combined
        ServerSignature On
        Alias /sf /usr/share/php/data/symfony/web/sf
</VirtualHost>
```

---

### Post by milwell on 2008-02-13
> **milwell said:**
> me too, i already have the directory 
allowoverride all 
command

but it's still not working

using ubuntu 7.10

```

<Directory /home/sysadmin/QA/web >
    AllowOverride All
    Allow from all
</Directory>


<Directory /home/sysadmin/QA >
    AllowOverride All
    Allow from all
</Directory>


<VirtualHost *>
        ServerAdmin webmaster@mail.ksk
        ServerName manufacturing.ksk
        DocumentRoot /home/sysadmin/symfony/QA/web
        ErrorLog /var/log/apache2/error-manufacturing.ksk.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel debug
        CustomLog /var/log/apache2/manufacturing.ksk.log combined
        ServerSignature On
        Alias /sf /usr/share/php/data/symfony/web/sf
</VirtualHost>
```

had a typo 
<Directory /home/sysadmin/QA/web >

should be 
<Directory /home/sysadmin/symfony/QA/web>



and now it works.

---

