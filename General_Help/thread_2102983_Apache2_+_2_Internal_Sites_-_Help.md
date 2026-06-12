---
title: "Apache2 + 2 Internal Sites - Help?"
date: 2013-01-08
forum: General Help
---

### Post by ThePhantom0114 on 2013-01-08
Alright, so I have ran into a problem. I'm fairly new with linux, and never used Apache before this past month, so I'm kinda lost. I have my server at home running 12.04.1 Server, and everything has been running great. 

Now, I have Virtualbox set up on it and I run a VM 24/7. I use phpvirtualbox to manage it. I installed Apache2 and got the vbox page working fine on it, with the default Apache set up. Hitting the box directly, I still got the Apache test page, but when I used [http://server/phpvirtualbox](http://server/phpvirtualbox), it worked. Thats perfect. Now I went to install a prebuilt web package, and it goes in /var/www/example/www. It's meant to keep its same structure. In the guide I followed to set that up, it told me to use apache2/available-sites and disable the default page, add a new one, and enable it. I used:

sudo a2dissite default
sudo a2ensite example
sudo a2enmod rewrite
sudo service apache2 restart

After I did this, the new page worked perfectly as the root ([http://server](http://server)), but I couldnt access phpvirtualbox anymore. So I added another file in available-sites, but I'm not sure what to change to let it get to phpvirtualbox using the same host name... I tried changing the port ( <VirtualHost *.81> at the top, but that didnt help.

Any thoughts? And thanks for any advice.

---

### Post by btindie on 2013-01-09
It sounds like by enabling that other site it's changed the DocumentRoot that apache uses, from /var/www to /var/www/example/www.

You could go down the route of having multiple Virtual Servers. At it's most basic form you just need to add an entry to your /etc/hosts file mapping the hostname to your IP address then configure another site specifying the ServerName.

For a quick fix I think it would be sufficient to add the following to a new file /etc/apache2/conf.d/phpvirtualbox
```

Alias /phpvirtualbox/ "/var/www/phpvirtualbox/"
<Directory /var/www/phpvirtualbox/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride None
  Order Allow,Deny
  Allow From All
</Directory>

```

Reload Apache to make the config active ```
sudo service apache2 reload
```

Then access it as [http://server/phpvirtualbox/]("http://server/phpvirtualbox/")

If you want to change the port phpvirtualbox responds on then you'll also need to modify /etc/apache2/ports.conf as you need to tell Apache to listen on port 81. Add the following to that file
```
NameVirtualHost *:81
Listen 81
```

and then restart Apache
```
sudo service apache2 restart
```

---

