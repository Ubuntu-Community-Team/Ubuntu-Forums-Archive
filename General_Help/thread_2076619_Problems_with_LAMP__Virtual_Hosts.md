---
title: "Problems with LAMP  Virtual Hosts"
date: 2012-10-26
forum: General Help
---

### Post by Randy Schilling on 2012-10-26
I've just installed Ubuntu LAMP.

I want to setup two virtual hosts.
I have two files, default and rjs357, in sites-available, with links to files in sites-enabled.
When I restart apache using $apachectl -k restart I get a warning
NameVirtualHost *:80 has no VirtualHosts
and when I restart apache with $/etc/init.d/apache2 restart, the warning appears twice.
Why are these warnings appearing when I have virtual hosts setup already?

My default virtual host file came out of installation looking like this:
<VirtualHost *>
        ServerAdmin snip

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

This seems to be ALMOST working; meaning,
[http://localhost/]("http://localhost/phpinfo.php")index.html and
[http://localhost/]("http://localhost/phpinfo.php")[phpinfo.php]("http://localhost/phpinfo.php") 
brings up the expected pages BUT
[http://localhost/]("http://localhost/phpinfo.php")
is redirected to a
[http://localhost/apache2-default/](http://localhost/apache2-default/)
which my browser cannot find.
I expected  [http://localhost/]("http://localhost/phpinfo.php") to bring up index.html.
At this time I don't know what
these <Directory> </Directory> statements are doing but I'll experiment them
later on once I get things going.

My second virtual host, rjs357, looks like this:

<VirtualHost *>
        ServerName   rjs357.com
       ServerAdmin  snip
        DocumentRoot /var/www/rjs357/
        ErrorLog     /var/log/apache2/rjs357/error.log
        CustomLog    /var/log/apache2/rjs357/access.log
</VirtualHost>

is NOT working.  
[http://rjs357.com/index.html](http://rjs357.com/index.html) and
bring up the default index.hml and
[http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php) 
does not contain the correct Document_Root.
How do I fix this so that [http://rjs357.com/](http://rjs357.com/) the index.html, 
in /var/www/rjs357/, which is the expected behavior.

Also, please make any suggestions, refs to read and so on, to improve my configuration.
For instance, would it be better to replace NameVirtualHost *:80 in ports.conf
with NameVirtualHost ip:80 where ip is my ps's ip address?

Thanks, grateful to have this forum, Randy

---

### Post by Lars Noodén on 2012-10-26
I've copied the config files locally and get a syntax error in the second.  Try checking the configuration file's syntax.  

```

apachectl configtest

```

(  It also helps to obsessively check the error logs whenever making a configuration change.  )

There is a problem with the way you have [CustomLog](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#customlog).  The line must also include the format.  You can cut and paste the one from the manual if you have no preference.  Otherwise you can try drafting your own [log format](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats).

```

CustomLog /var/log/apache2/rjs357/access.log "%h\t%l\t%u\t%t\t%r\t%>s\t%b"

```

Also, putting the above configurations inside [****code][/code] tags will help with on-screen readability.

About the no virtual hosts warning, try starting the second vhost by specifying the port explicitly.

<VirtualHost *:80>

By the way, are you going to serve HTTPS?

---

### Post by Randy Schilling on 2012-10-26
I found the reference
[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)
and reset my second virtual host, /etc/apache2/sites-available/rjs357 with a lint to
a file in /etc/apache2/sites-enabled, in this way
```
<VirtualHost *>
        ServerAdmin snip
        ServerName rjs357.com  
        DocumentRoot /var/www/rjs357/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/rjs357/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/rjs357/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/rjs357/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```


The information page contains mixed and confusing data:
It shows ServerName rjs357.com which shows that my 
/etc/apache2/sites-available/rjs357 file is being read
but the DocumentRoot command is not being honored.

What am I doing wrong?

---

### Post by Randy Schilling on 2012-10-26
I've corrected my CustomLog statement and 
```
 $apachectl configtest 
```
gives only the original warning "NameVirtualHost *:80 has no VirtualHosts"

---

### Post by Lars Noodén on 2012-10-26
You have them both pointing to /var/www, though the second one points to /var/www/rjs357/.  In otherwords, the second vhost's DocuemntRoot is a subdirectory of the first vhost's DocumentRoot.  

I would make another subdirectory for the first vhost, /var/www/default or something.

---

### Post by Randy Schilling on 2012-10-26
I've set
```
 DocumentRoot /var/www/rjs357/ 
```
which contains index.html distinct from that of my default index.html.
But [http://rjs357.com/](http://rjs357.com/) and [http://rjs357.com/index.html](http://rjs357.com/index.html) bring the
index.html of my default site.; this is consistent with the
table in [http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php)
shows Document_Root to be /var/www/ which is that of my default site.
This is why I said the DocumentRoot statement of rjs357 is not being honored.

Thanks for the [code]  tip.

---

### Post by Randy Schilling on 2012-10-26
ok, read your post after my posting my last post.
Will try idea in you post and get back.

---

### Post by Randy Schilling on 2012-10-26
I created /var/www/default/,
moved appropriate index.html and phpinfo.php there,
made the the change to DocumentRoot in /etc/apache2/sites-available/default,
passed the syntax test and restarted.

Now DocumentRoot of rjs357.com comes up as /var/www/default/
when i've directed it to /var/www/rjs357/.

Please advise.

---

### Post by Randy Schilling on 2012-10-26
I guess https refers to ssl and security, which I have to learn about.
For now though, I don't thinks there's any reason for me to be concerned with security, 
no transactions taking place.

---

### Post by Lars Noodén on 2012-10-26
> **Randy Schilling said:**
> Now DocumentRoot of rjs357.com comes up as /var/www/default/
when i've directed it to /var/www/rjs357/.


I'm able to duplicate the error using your configurations above, but am missing something obvious.  I thought it might be ServerName, but that has no effect.

---

### Post by Lars Noodén on 2012-10-26
Check to make sure that what you have in ServerName matches the shortcut you actually put into /etc/hosts.  If they do not match, then you will automatically get served the default site instead of the one you want.  Making sure that ServerName is in harmony with /etc/hosts fixed the problem with my copies of your config files.

---

### Post by Randy Schilling on 2012-10-26
That's a great effort.  Thanks.

---

### Post by Randy Schilling on 2012-10-26
This is my current /etc/host file,
```

127.0.0.1    localhost
127.0.1.1    hpc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```I didn't do anything to this file previously, and I'm not sure what change
you want me to make now.

---

### Post by Randy Schilling on 2012-10-26
I added the line
```

67.167.150.157 rjs357.com

```
to my /etc/hosts and  restarted apache.  No help.

/etc/www/default/ still show up as document root in [http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php).
67.167.150.157 is my ip address and it shows up in [http://rjs357.com/phpinfo.php](http://rjs357.com/phpinfo.php) as
REMOTE_ADDR and SERVER_ADDR, though I haven''t specified my ip anywhere
in my apache configurations.

---

### Post by Randy Schilling on 2012-10-26
This works!
My ports.conf contains
```

NameVirtualHost *:80
Listen 80

```

So I guessed the change  <VirtualHost *>   to <VirtualHost *:80>  in both my
default and rjs357 virtual host files (which are located in /etc/apache2/sites-available).

Does this make sense to you?   Is this the best way?

My sincere apology if this should have been obvious.

---

### Post by Randy Schilling on 2012-10-26
I no longer get the error "NameVirtualHost *:80 has no VirtualHosts"
when I restart apache,
and by changing * to *:80, as explained in my previous post, 
I've connected my virtual hosts, default and rjs357, to the settings in my ports.conf.

Do you agree?

---

### Post by CharlesA on 2012-10-26
Hi,

Virtualhosts are supposed to be defined in /etc/apache2/sites-avalible/nameofvirtualhost, not /etc/apache2/ports.conf. You can add them to ports.conf but it will make it more difficult to troubleshoot issues.

Also: I have removed your email address from your post, as it isn't really necessary to troubleshooting your config.

Here's what one of my virtualhosts looks like:

```
charles@Precise:~$ cat /etc/apache2/sites-available/charlesa.net
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName charlesa.net
        DocumentRoot /home/charles/site/charlesa.net/
        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

---

### Post by sandyd on 2012-10-26
> **CharlesA said:**
> Hi,

Virtualhosts are supposed to be defined in /etc/apache2/sites-avalible/nameofvirtualhost, not /etc/apache2/ports.conf. You can add them to ports.conf but it will make it more difficult to troubleshoot issues.

Also: I have removed your email address from your post, as it isn't really necessary to troubleshooting your config.

Here's what one of my virtualhosts looks like:

```
charles@Precise:~$ cat /etc/apache2/sites-available/charlesa.net
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName charlesa.net
        DocumentRoot /home/charles/site/charlesa.net/
        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
> **Randy Schilling said:**
> This works!
My ports.conf contains
```

NameVirtualHost *:80
Listen 80

```

So I guessed the change  <VirtualHost *>   to <VirtualHost *:80>  in both my
default and rjs357 virtual host files (which are located in /etc/apache2/sites-available).

Does this make sense to you?   Is this the best way?

My sincere apology if this should have been obvious.
Note that the ports.conf file by default contains NameVirtualHost - you have to have it set somewhere in order to use virtual hosts. Your current setup is correct.
It is set in there, instead of the virtual hosts to avoid confusion :)

---

### Post by CharlesA on 2012-10-26
> **sandyd said:**
> Note that the ports.conf file by default contains NameVirtualHost - you have to have it set somewhere in order to use virtual hosts.
It is set in there, instead of the virtual hosts to avoid confusion :)
Makes sense. I think that was where I ran it originally, but found a good thread on it somewhere around here, but I cannot recall the name of it. :|

---

### Post by sandyd on 2012-10-26
> **CharlesA said:**
> Makes sense. I think that was where I ran it originally, but found a good thread on it somewhere around here, but I cannot recall the name of it. :|

I don't use apache anymore, so I wouldn't know :) . (/me moved to using Caucho Resin app servers)

---

### Post by Randy Schilling on 2012-10-26
My virtual hosts are defined in separate files, default and rjs357, in /etc/apache2/sites-available, which are linked to files in .../sites-enabled.  They're not defined in ports.conf.

The lesson behind this thread is that the value of X in virtual host headers 
```
<VirtualHost X>...</VirtualHost>
```
must agree with the setting Y in 
```
NameVirtualHost Y
```.
If one of them is *:80 then the other must also be *:80.
I guess * would work as well, but both must be *.
I guess ip:80 would work too, again, settings must agree.

Thanks for removing my email.

Everything seems to be working fine, both by virtual hosts are working as
I expect them to work so I'm going to mark this thread as solved.

---

### Post by Randy Schilling on 2012-10-26
what happened to the rest of this thread?

---

### Post by CharlesA on 2012-10-26
Rest of the thread? Looks normal to me.

---

### Post by Randy Schilling on 2012-10-26
I'm going from memory here (which is often a mistake for me) but I think there
is an inconsistency in the way apache2 is delivered to us.  
/etc/apache2/ports.conf contains
```
NameVirtualHost *:80
```whereas /etc/apache2/sites-available/default contains
```

NameVirtualHost *
<VirtualHost *>
...
</VirtualHost>

```I think it would be better if *:80 or * where used throughout the distribution.

---

### Post by CharlesA on 2012-10-26
Mine says this:

```
charles@Precise:~$ cat /etc/apache2/ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

```
charles@Precise:~$ cat /etc/apache2/sites-available/default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by Randy Schilling on 2012-10-26
Google /etc/apache2/sites-available/default
or go directly to
[http://www.howtoforge.com/forums/showthread.php?t=3220](http://www.howtoforge.com/forums/showthread.php?t=3220)
to see the file that comes out of the installation.

---

### Post by sandyd on 2012-10-26
> **Randy Schilling said:**
> I'm going from memory here (which is often a mistake for me) but I think there
is an inconsistency in the way apache2 is delivered to us.  
/etc/apache2/ports.conf contains
```
NameVirtualHost *:80
```whereas /etc/apache2/sites-available/default contains
```

NameVirtualHost *
<VirtualHost *>
...
</VirtualHost>

```I think it would be better if *:80 or * where used throughout the distribution.

/etc/apache2/sites-available/default should not have NameVirtualHost * in it.

and also, the forum thread you mentioned is not even for Ubuntu. It is for ISPConfig.

---

### Post by CharlesA on 2012-10-27
> **sandyd said:**
> /etc/apache2/sites-available/default should not have NameVirtualHost * in it.

That is how I remember it too. I just installed apache2 on one of my 12.04 test boxes and that is completely correct.

> Also, by default, there is no /etc/apache2/sites-avaliable/default file, only a /etc/apache2/sites-avaliable/000-default file, which is symlinked to ../sites-enabled via a2ensite

I just installed Apache on my test box and the symlink is set up like this:

```
charles@Tardis:~$ ls -l /etc/apache2/sites-available/
total 12
-rw-r--r-- 1 root root  950 Feb  6  2012 default
-rw-r--r-- 1 root root 7469 Feb  6  2012 default-ssl
charles@Tardis:~$ ls -l /etc/apache2/sites-enabled/
total 0
lrwxrwxrwx 1 root root 26 Oct 27 03:07 000-default -> ../sites-available/default

```

Contents of the file:

```
charles@Tardis:~$ cat /etc/apache2/sites-available/default
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
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

ports.conf:

```
charles@Tardis:~$ cat /etc/apache2/ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

---

### Post by Randy Schilling on 2012-10-27
I agree Sandyd,
> /etc/apache2/sites-available/default should not have NameVirtualHost * in it.This is true because /etc/apache2/ports.conf contains 
```
NameVirtualHost *:80 
```In addition,  /etc/apache2/sites-available/default, should be changed from
```
<VirtualHost *> ...</VirtualHost>    
```to  
```
 <VirtualHost *:80>  ...</VirtualHost>
```.
If you don't make this change then upon restart apache2 will return a warning
that there are no virtual hosts assigned to *:80 (which is correct!).
I think another alternative is to change ports.conf to
```
NameVirtualHost *
```and leave the default virtual host as is (with * not *:80) but I have not tested this.

Lastly, my apache2 installed with /etc/apache2/sites-available/default linked to 
/etc/apache2/sites-enabled/000-default.

---

