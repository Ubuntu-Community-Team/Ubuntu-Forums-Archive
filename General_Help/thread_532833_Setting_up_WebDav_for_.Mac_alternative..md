---
title: "Setting up WebDav for .Mac alternative."
date: 2007-08-23
forum: General Help
---

### Post by JungMin on 2007-08-23
I am following the guide ([http://www.tnpi.biz/computing/mac/tips/idisk/idisk-v2.shtml](http://www.tnpi.biz/computing/mac/tips/idisk/idisk-v2.shtml))  to set up my own .Mac alternative.

I have been following the above guide, but it doesnt go into too much detail about how to install and setup WebDav.  So I was using a similar How-To here ([http://ubuntuforums.org/showthread.php?t=119228&highlight=webdav+apache2](http://ubuntuforums.org/showthread.php?t=119228&highlight=webdav+apache2)).

I added these config lines to Apache's config files:

     ```
DavLockDB /var/run/webdav/DavLock
      
     <VirtualHost *:80>
           ServerName idisk.cadillac.net
           DocumentRoot "/home/idisk/html"
     </VirtualHost>
      
     <Directory "/home/idisk/html">
           Dav on
           AuthType Digest
           AuthName iTools
           AuthDigestDomain "/"
           AuthDigestFile /home/idisk/WebDavUsers
           AuthGroupFile /home/idisk/WebDavGroups
           Options None
           AllowOverride None
            
           <LimitExcept GET HEAD OPTIONS>
                 require valid-user
           </LimitExcept>
            
           Order allow,deny
           Allow from All
     </Directory>
```


But when I restart apache, I get this.....

 ```
Forcing reload of web server (apache2)...                                    Syntax error on line 682 of /etc/apache2/apache2.conf:
Invalid command 'AuthDigestDomain', perhaps misspelled or defined by a module not included in the server configuration
```


Can anyone help me out?? 
Cheers...

---

### Post by JungMin on 2007-08-23
Actually,

This is damn near impossible.  Well, i'm sure its not.....but i think its a bit over my head.  I have so many questions, I don't even know where to start.  
I use my Ubuntu machine as my home server and access it with my media center and HOPEFULLY, with my MacBook - both at home and away.  To sync my calendars, backups, iDisk, etc.

---

