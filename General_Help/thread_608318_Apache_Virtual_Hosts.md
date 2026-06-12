---
title: "Apache Virtual Hosts"
date: 2007-11-09
forum: General Help
---

### Post by bullines on 2007-11-09
Hi!

I'm trying to set up a couple of development websites on my Gutsy machine.  The problem I'm having is as follows.

My paths are:

/home/me/web/site1.com
/home/me/web/site2.com

In /etc/apache2/sites-available I have:

```

# domain: site1.com
# public: /home/me/web/site1.com/

<VirtualHost *>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@site1.com
  ServerName  site1.com
  ServerAlias www.site1.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /home/me/web/site1.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/me/web/site1.com/logs/error.log
  CustomLog /home/me/web/site1.com/logs/access.log combined

</VirtualHost>

```

and:

```

# domain: site2.com
# public: /home/me/web/site2.com/

<VirtualHost *>
  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@site2.com
  ServerName  site2.com
  ServerAlias www.site2.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /home/me/web/site2.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/me/web/site2.com/logs/error.log
  CustomLog /home/me/web/site2.com/logs/access.log combined
</VirtualHost>

```

I run 'sudo a2ensite /etc/apache2/sites-available/site1.com' and  'sudo /etc/apache2/sites-available/site2.com'.  Then I run 'sudo /etc/init.d/apache2 reload'.  I update my /etc/hosts so that it contains:

```

127.0.0.1 localhost localdomain localhost ubuntu1 
127.0.0.1 www.site1.com
127.0.0.1 www.site2.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I cannot browse to either [www.site1.com](www.site1.com) or [www.site2.com](www.site2.com).  Even weirder is that I can't even reach [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/).  If I do a 'sudo /etc/init.d/apache2 restart', I get:

```

 * Restarting web server apache2                                                httpd (pid 6726?) not running

```

If I then do a2dissite for site1.com and site2.com and then run 'sudo /etc/init.d/apache2 reload' followed by 'sudo /etc/init.d/apache2 restart', I'm at least able to access [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) again.

What am I doing wrong?

Thanks in advance.

---

### Post by bullines on 2007-11-10
*bump*

---

