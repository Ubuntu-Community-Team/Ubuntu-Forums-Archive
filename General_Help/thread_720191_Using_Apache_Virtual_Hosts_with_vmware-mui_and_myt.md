---
title: "Using Apache Virtual Hosts with vmware-mui and mythweb"
date: 2008-03-10
forum: General Help
---

### Post by cknight725 on 2008-03-10
I have read the following docs on using Virtual hosts with my various web-interfaces on my Mythbuntu and VMWare server.

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)
[http://www.apacheweek.com/features/vhost](http://www.apacheweek.com/features/vhost)

Basically what I would like to setup name-based virtual hosts for my "mythweb" and " vmware-mui" interfaces.  I'm confused because it looks like mythweb sticks its config files in the normal apache2 locations, while vmware-mui's httpd.conf is elsewhere.

Can I do my Virtual Host config in a "one-stop shop" by simply editing the /etc/apache2/httpd.conf?

For what its worth, I think this is the basic code I want to use:
```
 # Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /var/www/mythweb
ServerName mythweb.mydomain.com

# Other directives here

</VirtualHost>

<VirtualHost *:80>
DocumentRoot /usr/lib/vmware-mui/apache/htdocs
ServerName vmwareweb.mydomain.com

# Other directives here

</VirtualHost>
```

I'm running Mythbuntu 7.10 ....

---

