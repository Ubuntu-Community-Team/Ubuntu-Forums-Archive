---
title: "Apache with multiple domains + bind on local network"
date: 2019-08-05
forum: General Help
---

### Post by mcp1766 on 2019-08-05
Hello,
I'm trying to set up in my local network apache virtual domains and configure bind to access the content.  what I did :
[LIST]
[*]install apache + firewall + bind 
[*]add Apache, 80, 883 to the firewall 
[*]tested welcome page "it works" ok 
[*]set up virtual host (siteA.com) 
[*]created in var/www a folder siteA.com with subfolder public_html 
[*]created an index.html file 
[*]changed permission (chmod -R 755 on /var/www 
[*]created in /etc/apaches2/sites-available the file siteA.com.conf with : 
[/LIST]
```

<VirtualHost *:80>
    ServerAdmin webmaster@siteA.com
    ServerName siteA.com
    ServerAlias www.siteA.com
    DocumentRoot /var/www/siteA.com/public_html
    ErrorLog $(APACHE_LOG_DIR)/error.log
    CustomLog $(APACHE_LOG_DIR)/access.log combined
</VirtualHost>

``` 
[LIST]
[*]enabled the new vhost file (a2ensite siteA.com.conf) 
[*]reloaded apache 
[*]created a folder for my hosted zone files in /etc/bind/hostedzones 
[*]created in that folder a subfoler siteA.com 
[*]copied /etc/bind/db.local => /etc/bind/hostedzones/siteA.com/db.siteA 
[*]edited db.siteA with : 
[/LIST]
```

$ORIGIN siteA.com.
$TTL 604800
@ IN SOA siteA.com. webmaster.siteA.com. (
      2009080501;
      604800;
      86400;
      2419200;
      604800);
   IN NS siteA.com.
localhost    IN A 127.0.0.1
siteA.com. IN A 192.168.0.19
www         IN A 192.168.0.19
ftp            IN A 192.168.0.19

```
[LIST]
[*]edited /etc/bind/named.conf.local and add : 
[/LIST]
```

zone "siteA.com" {
 type master;
 file:"/etc/bind/hostedzones/siteA.com/db.siteA";

```
[LIST]
[*]reloaded bind 
[*]temporary edited /etc/resolv.conf and changed "nameserver" to 192.168.0.19 
[*]type in the browser siteA.com => get welcome page 
[*]tried from another computer => page not found 
[*]changed the /etc/resolv.conf and putted "nameserver 192.168.0.19" => nok 
[*]then restored back resolv.conf 
[*]added /etc/hosts 192.168.0.19 siteA.com => ok 
[/LIST]
So far how can I configure other computer to acces the virtual domain with dns (I mean without adding the address in the hosts file) ?
It is working only from the computer where I installed and configured all the stuff but from other computer it is not working (only if a add the address in hosts file).  If a have 3 computers it is not a big deal but with more it become hardious to edit hosts file one by one...  

If someone can also give the procedure (particulary the dns part)  to do the same (apache + vhost + bind) for a purchased domain by Namecheap it would be nice.  I already set up the A records with my public IP but dont know how to configure the stuff on my lan computer (my firewall accepts 80 443 22 25).
Thank.

---

