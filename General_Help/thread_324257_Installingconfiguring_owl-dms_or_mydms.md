---
title: "Installing/configuring owl-dms or mydms"
date: 2006-12-23
forum: General Help
---

### Post by redyaky on 2006-12-23
Hi!

I'm trying to set up a dms server at home. I'm looking at 2 packages, owl-dms and mydms, both of which use PHP and mySQL which are installed on my machine from but may not be configured correctly (particularly mySQL). 

Does anyone have any experience working with one of these dms packages? Perhaps someone knows a better alternative. 

Any help would be greatly appreciated. Thanks!

---

### Post by nhenry on 2008-01-12
I'd reccomend mydms

Install a [LAMP Server]("https://help.ubuntu.com/community/ApacheMySQLPHP")

from command line:
administrator@ubuntu:~$ sudo apt-get install mydms
administrator@ubuntu:~$ sudo ln -s /usr/share/mydms/www /var/www/dms

Go to [http://localhost/mydms]("http://localhost/mydms")
Username: admin
Password: admin

---

### Post by handband2 on 2008-02-21
I've tried installing MyDMS through apt-get and manually.  Either way I get the following errors:
> 
Forbidden

You don't have permission to access /mydms on this server.

A few things I've tried
[LIST]
Virtual Hosts from [here]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[/LIST]
[LIST]
Change permissions "chmod -R 755"
[/LIST]

Any other ideas why this message is still showing up?

---

### Post by jzimmerman on 2008-04-02
By default the mydms apache config file is set to deny all but localhost (127.0.0.1)

Open /etc/apache2/sites-available/mydms in your favorite editor.  And make it look like this...

```
Alias /mydms "/usr/share/mydms/www"
<Directory "/usr/share/mydms/www">
php_admin_flag register_globals on
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
# Deny from all
Allow from all
# Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
```

This comments out the statements to Deny from all and to only allow connections from the localhost.  It also adds the directive to allow from all.

Please be aware what implications this has (i.e. anyone that can access your webserver can pull up the application).

Now restart apache using 'sudo /etc/init.d/apache2 restart'

So [http://yourservernamehere/mydms](http://yourservernamehere/mydms) should now bring up the login screen.

---

