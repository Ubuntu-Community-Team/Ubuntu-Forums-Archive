---
title: "Apache - mapping URLS"
date: 2005-08-10
forum: General Help
---

### Post by batterhead on 2005-08-10
Hi all,

I used the instruction here: [http://ubuntuguide.org/#mapURLstofoldersoutsidewww](http://ubuntuguide.org/#mapURLstofoldersoutsidewww)

to map URLs to a directory outside of /var/www

When I try to access the directory I mapped I get this error:

```
Forbidden

You don't have permission to access /www/test.php on this server.
Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4 Server at localhost Port 80
```

Here is what my file looks like:

```
Alias /www /home/ckline/www/

<Directory /home/ckline/www/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>
```

Thanks for any help

---

### Post by crmanski on 2005-08-10
I would look at the ACLs on that directory the  files with are.  Make sure that they are readable by all (others).

This part mentions this.
[http://ubuntuguide.org/#changefilesfolderspermissions](http://ubuntuguide.org/#changefilesfolderspermissions)

---

### Post by batterhead on 2005-08-16
Thanks. Just needed to set the directory permission so that EVERYONE had execute  - 755. This is secure, no?

---

