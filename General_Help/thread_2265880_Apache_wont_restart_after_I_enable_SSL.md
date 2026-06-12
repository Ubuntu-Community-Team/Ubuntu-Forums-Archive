---
title: "Apache wont restart after I enable SSL"
date: 2015-02-18
forum: General Help
---

### Post by stephen66 on 2015-02-18
Once I a2enmod the ssl moduleand restart apache I get the following error:

```
 * Restarting web server apache2                                                AH00548: NameVirtualHost has no effect and will be removed in the next release /etc/apache2/ports.conf:14
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:443
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
```

To stop it I can either disenmod or comment out the ifmodule lines in the ports.conf file

```
Listen 80
#<IfModule mod_ssl.c>
#    Listen 443
#</IfModule>


<IfModule mod_gnutls.c>
        Listen 443
</IfModule>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```


Any help would be much appreciated.

---

