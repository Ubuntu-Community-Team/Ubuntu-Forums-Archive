---
title: "Local keeps redirecting to https: :-("
date: 2021-08-20
forum: General Help
---

### Post by dbee on 2021-08-20
I'm trying to install wordpress on local from live. My local keeps redirecting me to https...

i'm not sure whether it's an ubuntu apache issue or a WP issue. Since no-one ever answers on wordpress.org forum support. 

I thought i'd post on ubuntuforums... 

What i've done so far...

1. scoured the apache config files for any http -> https redirects in .conf sites-enabled or sites-available...

This is what my site config file looks like ...
```

<VirtualHost *:80>
    ServerAdmin dara@mysite.com
    ServerName 127.0.0.1
    ServerAlias www.mysite
    DocumentRoot /var/www/mysite
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

2. used WP cli to replace any https:// with http:// full path links in the db

```
wp search-replace https:// http:// --all-table
```

3. did a dump of the db to find whether wordpress is storing any https:// full path links...

```
mysqldump -u myuser --no-create-info --extended-insert=FALSE databasename | grep -i "<https://>"
``` 

4. I've disabled the ssl mod in apache
 
```
a2dismod ssl
```

5. I've parked the really-simple-ssl plugin by renaming the plugin folder to really-simple-ssl-park

6. I've deleted the .htaccess file but not before trying to explicity redirect https to https in the file. No luck.

can anyone suggest another solution here?

I can see the login.php page fine. but when i follow the link to the homepage i'm served [https://localhost](https://localhost) automatically...

help!

---

### Post by Holger_Gehrke on 2021-08-20
Have you checked the settings of your browser ? In Firefox you'll find the https-only mode at the very bottom of about:preferences#privacy . If this mode is on FF will upgrade any connection to https automatically unless you have an exceptions defined for a specific host. I don't use chrom{e,ium}, but I think there's something similar on that ...

Holger

---

### Post by dbee on 2021-08-20
Thanks Holger.

Turned off safe browsing on chrome and set localhost to localhost 'Insecure Content' to 'Allow'

Still redirects to https.

I guess i'll have to install an SSL cert and see whether that makes any difference.

---

