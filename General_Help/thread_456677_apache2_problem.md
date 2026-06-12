---
title: "apache2 problem"
date: 2007-05-27
forum: General Help
---

### Post by kain2396 on 2007-05-27
Hi everyone

I'm trying to get apache2 working on a Feisty install. It gives me this message:

```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```


I've done this modification to default in sites-available/

```

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName <ipaddress>

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
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```

And this is my hosts file:

```
127.0.0.1       localhost <ipaddress>
127.0.1.1       IESF-NET

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

With <ipaddress> being my actual ipaddress.

Attempts to connect to localhost go through, attempts to go through [http://ipaddress](http://ipaddress) time out.

Any help would be greatly appreciated, as the people in #apache don't seem to talkative.

---

### Post by kain2396 on 2007-05-28
Am I asking this in the wrong forum?

---

