---
title: "problems with apache virtual host, everything works fine until 4th is added"
date: 2008-02-06
forum: General Help
---

### Post by phillips321 on 2008-02-06
hi guys, 

i have my server currently running 3 websites and i would like to add another. When i copy one of the virtual host files found in /etc/apache2/sites-available and change the details for the new website and then run "sudo a2ensite" the link gets created fine, when i then reload apache i get a failure and none of the sites load.

please see the following for an output of what is happening....
```
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ ls
default  www.gagj.co.uk  www.phillips321.co.uk  www.rickardinteriors.com  www.rtfa.co.uk
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ cat www.rickardinteriors.com 
#
# rickardinteriors.com
#
<VirtualHost *>
        ServerAdmin postmaster@rickardinteriors.com
        ServerName www.rickardinteriors.com
        ServerAlias rickardinteriors.com

        # Indexes + Directory root
        DirectoryIndex index.html
        DocumentRoot /var/www/rickardinteriors.com/

        # CGI Directory
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Location usr/lib/cgi-bin/>
                Options +ExecCGI
        </Location>

        # LogFiles
        ErrorLog /var/www/rickardinteriors.com/logs/error.log
        CustomLog /var/www/rickardinteriors.com/logs/access.log combined
</VirtualHost>
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ sudo a2ensite www.
www.gagj.co.uk            www.phillips321.co.uk     www.rickardinteriors.com  www.rtfa.co.uk
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ sudo a2ensite www.rickardinteriors.com 
Site www.rickardinteriors.com installed; run /etc/init.d/apache2 reload to enable.
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                                                   [Wed Feb 06 07:35:39 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd not running, trying to start
                                                                                                    [fail]
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ sudo a2dissite www.rickardinteriors.com 
Site www.rickardinteriors.com disabled; run /etc/init.d/apache2 reload to fully disable.
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                                                   [Wed Feb 06 07:36:09 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd not running, trying to start
                                                                                                    [ ok ]
phillips321@LinuxHTTPVM:/etc/apache2/sites-available$ 

```

---

### Post by phillips321 on 2008-02-06
i have just figured out what is causing this problem, the directory where the logs should have been going was not created so it killed the whole of apache!!!!! not good, guess i'll have to change the location of the logs folder do stop users from deleting them

---

