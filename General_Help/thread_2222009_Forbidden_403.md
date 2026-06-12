---
title: "Forbidden 403"
date: 2014-05-04
forum: General Help
---

### Post by alfirdaous on 2014-05-04
Hello everybody,

I have 3 websites in my localhost, and I tried to access them but it gives 403 error, this is the website file:

```

<VirtualHost *:80>
        ServerAdmin alfirdaous@gmail.com
        DocumentRoot /home/alfirdaous/NetBeansProjects/
        # Nom d'utilisateur, nom du groupe, généralement identique
#       SuexecUserGroup alfirdaous alfirdaous
        <Directory />
                Options FollowSymLinks
#               AllowOverride None
                AllowOverride All

        </Directory>
#       <Directory /home/alfirdaous/NetBeansProjects/Alfirdaous/>
#               Options Indexes FollowSymLinks MultiViews
#               AllowOverride None
#               Order allow,deny
#               allow from all
#       </Directory>

        <Directory /home/alfirdaous/NetBeansProjects/*/www/>
#                Options Indexes FollowSymLinks MultiViews
                Options FollowSymLinks
                AllowOverride All
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

        <Directory /home/alfirdaous/NetBeansProjects/Tests/PHP/x/>
                Order deny,allow
                 Deny from all
        </Directory>

                                                                                                                    1,1           Top

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Thanks in advance

---

### Post by mcduck on 2014-05-04
Check the permissions of the files themselves, and the directories containing them. Since the files are located in your home, I assume they are also owned by your user account. You need to have read access for "others" on the files, and read & execute on directories.

---

