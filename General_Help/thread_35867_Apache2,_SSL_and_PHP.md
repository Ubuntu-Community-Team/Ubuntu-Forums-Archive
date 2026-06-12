---
title: "Apache2, SSL and PHP"
date: 2005-05-20
forum: General Help
---

### Post by ujay on 2005-05-20
I have the web site set up and working without problem  :) .  I added SSL support and apache 2 now listens on 80 and 443 :smile: .

# apache2 -D SSL -S

VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:443                  is a NameVirtualHost
         default server localhost.localdomain (/etc/apache2/sites-enabled/000-default-ssl:2)
         port 443 namevhost localhost.localdomain (/etc/apache2/sites-enabled/000-default-ssl:2)
*:80                   is a NameVirtualHost
         default server localhost.localdomain (/etc/apache2/sites-enabled/000-default:2)
         port 80 namevhost localhost.localdomain (/etc/apache2/sites-enabled/000-default:2)
Syntax OK :grin: 

PHP scripts work fine on normal http protocol, but fail to execute on https :? :  (Firefox pops up a download dialog).

I'm trying everything I can think of, so far with no success.  I'll keep looking, but if anyone here has any suggestions, i'm all ears.

---

### Post by ujay on 2005-05-20
Update - SSL PHP working. Problem was in redirect from http access to https access on protected scripts. ( used $server["server_addr"] instead of $server["server_name"] ).

---

