---
title: "Apache Virtual Hosts?"
date: 2006-11-18
forum: General Help
---

### Post by Airjoe on 2006-11-18
Hi

My linux box hosts two domains at the moment. I want it so that if someone goes to one of my domains, it points them into one directory, and if someone goes into another domain, it points them to the other directory. I host the nameservers for both domains. They both have the A record going to my IP address.

In my apache2.conf file, I did:
```

    NameVirtualHost *

    <VirtualHost *>
    ServerName www.atpdevelopment.com
    DocumentRoot /var/www
    </VirtualHost>

    <VirtualHost *>
    ServerName www.bluewavemartialarts.net
    DocumentRoot /var/www/BlueWave
    </VirtualHost>
```

Also, I think Webmin added:
```
Include /etc/apache2/sites-enabled/[^.#]*
```

However, if I go to the second domain, it still puts me into /var/www.

What am I doing wrong?

---

### Post by koenn on 2006-11-18
did you restart apache daemon after you changed the configuration ? 
If not, you're still running the previous config - changes should take effect after restarting the service

---

### Post by Airjoe on 2006-11-18
That would do it...

haha, thanks a ton!

---

### Post by jms1989 on 2006-12-06
I've had this happen to me before, it won't let me use multipule config files. Why?

---

### Post by clouserw on 2006-12-06
> **jms1989 said:**
> I've had this happen to me before, it won't let me use multipule config files. Why?

At the bottom of your apache2.conf there should be a line that says something like
```
Include /etc/apache2/sites-enabled/[^.#]*
```
That's the line that will include the other .conf files.

---

