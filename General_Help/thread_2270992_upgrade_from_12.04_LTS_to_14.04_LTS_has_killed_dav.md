---
title: "upgrade from 12.04 LTS to 14.04 LTS has killed dav_svn"
date: 2015-03-26
forum: General Help
---

### Post by frogman222 on 2015-03-26
I have the following site what was running perfectly while i was using 12.04.  Since upgrading to 14.04 LTS I have not been able to get subversion working in apache2.

Results from the "lsb_release -a"

```

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

```

the site file that was working in 12.04 LTS

```

<VirtualHost *:6842>

        ServerAdmin webmaster@hbws-svn
        ServerName hbws-svn

        DocumentRoot /media/data/subversion/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /media/data/subversion/>
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

        ErrorLog /media/data/homebrew/logs/svn/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /media/data/homebrew/logs/svn/access.log combined

    Alias /doc/ "/media/data/homebrew/docs/svn"
    <Directory "/media/data/homebrew/docs/svn">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    <Location /svn>
        DAV svn
        SVNParentPath /media/data/subversion
#       SVNIndexXSLT "/repos-web/view/repos.xsl"
        AuthType Basic
        AuthName "My Repositories"
        AuthUserFile  /media/data/www/.htpasswd
        Require valid-user
    </Location>

</VirtualHost>


```

I have followed all I can find through searching in forums but nothing seems to work.

when I try to simply load the site (sudo a2ensite hbws-svn.conf), I get the following response:

```

 * Reloading web server apache2                                                                                                                                                                                *
 * The apache2 configtest failed. Not doing anything.
Output of config test was:
AH00526: Syntax error on line 44 of /etc/apache2/sites-enabled/hbws-svn.conf:
Unknown DAV provider: svn
Action 'configtest' failed.
The Apache error log may have more information.

```

The apache error log shows:

```

[Fri Mar 27 09:04:40.221690 2015] [mpm_prefork:notice] [pid 14032] AH00169: caught SIGTERM, shutting down

```

I also tried (based on search results I found for the above) enabling the dav_svn module with "sudo a2enmod dav_svn" however this produces the following error when I attempt to restart the server
```

Output of config test was:
apache2: Syntax error on line 213 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/mods-enabled/dav_svn.load: Cannot load /usr/lib/apache2/modules/mod_dav_svn.so into server: /usr/lib/apache2/modules/mod_dav_svn.so: undefined symbol: ap_log_perror
Action 'configtest' failed.
The Apache error log may have more information.

```

There was nothing new in the apache2 logs.

Does anyone know what to do to progress from this?

Regards

Greg J

---

