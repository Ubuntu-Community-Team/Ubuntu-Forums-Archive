---
title: "I can't access var/www"
date: 2013-01-26
forum: General Help
---

### Post by jimeast on 2013-01-26
I installed Lampp on the 12.04 server, it used var/www as the localhost folder.  I don't have rights to var/www.  I supposedly have admin privileges and don't know what to do from here.  Any help will be greatly appreciated thanks.

---

### Post by sandyd on 2013-01-26
> **jimeast said:**
> I installed Lampp on the 12.04 server, it used var/www as the localhost folder.  I don't have rights to var/www.  I supposedly have admin privileges and don't know what to do from here.  Any help will be greatly appreciated thanks.
The /var/www folder is owned by www-data, which you won't have access to without elevated permisisons - see [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for a more comprehesive guide on permissions.

You should be able to copy files into /var/www if you use sudo to elevate your privelages, but that would require you to restore the permissions after copying.


There is a way that I think would be easier

Apache2 contains a module called mod_userdir luckily, which allows each user on the system to have a folder called public_html in their home directory in which apache2 serves from.

Replacing **username** with your username...
```

sudo a2enmod userdir
#Permissions must be at least 711 on all dirs
sudo chmod 711 /home
sudo chmod 711 /home/**username**
mkdir ~/public_html
chmod 0755 ~/public_html
```
There should now be a public_html folder in your home directory.

Lets add some kind of index page...
```

echo "Hi" > ~/public_html/index.html
```

Navigate to [http://localhost/](http://localhost/)~**your_username_here** (replacing your_username_here with your username).

You can determine your username by opening a terminal, and running ```

whoami
```

Finally, if you require php, 
```

sudo nano /etc/apache2/mods-available/php5.conf
```
place a '#' in front of php_admin_value engine Off so that it looks like
```

#php_admin_value engine OFf
```
Press Control +x to save, and run
```

sudo service apache2 restart
```

---

### Post by Lars Noodén on 2013-01-26
If you've installed Apache, then the default for the first vhost will be /var/www.  That can be changed or you can add other virtual hosts.  

If you are going to share write access with other users on the same machine, you can do it with groups:

```

sudo addgroup webmasters

sudo gpasswd --add jimeast  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

If you are the only one using the machine then you can do it either with groups as above or by chown by itself:

```

sudo chown -R jimeast:jimeast /var/www

```

---

### Post by Lars Noodén on 2013-01-26
> **sandyd said:**
> The /var/www folder is owned by www-data...

The default is that /var/www is owned by root.  If there is just one user of the machine, then chown for that user is fine.  

About the www-data group, that group is used for privilege separation by the HTTP daemon.  It should not be used for or by anything else. The only things that should be in that group are web servers.  Trying to use it in other ways defeats the security advantage.  If a group is needed, create a new one. www-data is already spoken for.

---

### Post by sandyd on 2013-01-26
> **Lars Noodén said:**
> The default is that /var/www is owned by root.  If there is just one user of the machine, then chown for that user is fine.  

About the www-data group, that group is used for privilege separation by the HTTP daemon.  It should not be used for or by anything else. The only things that should be in that group are web servers.  Trying to use it in other ways defeats the security advantage.  If a group is needed, create a new one. www-data is already spoken for.

Weird - its owned by www-ctdata on my laptop - must have probably changed it at some point or another

---

### Post by jimeast on 2013-01-26
Thank you this is very helpful :)




> **sandyd said:**
> The /var/www folder is owned by www-data, which you won't have access to without elevated permisisons - see [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for a more comprehesive guide on permissions.

You should be able to copy files into /var/www if you use sudo to elevate your privelages, but that would require you to restore the permissions after copying.


There is a way that I think would be easier

Apache2 contains a module called mod_userdir luckily, which allows each user on the system to have a folder called public_html in their home directory in which apache2 serves from.

Replacing **username** with your username...
```

sudo a2enmod userdir
#Permissions must be at least 711 on all dirs
sudo chmod 711 /home
sudo chmod 711 /home/**username**
mkdir ~/public_html
chmod 0755 ~/public_html
```
There should now be a public_html folder in your home directory.

Lets add some kind of index page...
```

echo "Hi" > ~/public_html/index.html
```

Navigate to [http://localhost/](http://localhost/)**your_username_here** (replacing your_username_here with your username).

You can determine your username by opening a terminal, and running ```

whoami
```

Finally, if you require php, 
```

sudo nano /etc/apache2/mods-available/php5.conf
```
place a '#' in front of php_admin_value engine Off so that it looks like
```

#php_admin_value engine OFf
```
Press Control +x to save, and run
```

sudo service apache2 restart
```

---

### Post by jimeast on 2013-01-26
Thanks, I think your solution is what I was looking for I also found sanydy's helpful.  I'm starting to like Ubuntu.

---

