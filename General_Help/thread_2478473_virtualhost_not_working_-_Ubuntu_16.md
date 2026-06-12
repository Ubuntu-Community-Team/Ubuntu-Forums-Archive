---
title: "virtualhost not working - Ubuntu 16"
date: 2022-08-27
forum: General Help
---

### Post by davidsanchezvasquez on 2022-08-27
Installed SMF forums on my Ubuntu server hosted on DigitalOcean in directory **/var/www/html/smf**

Added the below code in **/etc/apache2/apache2.conf **expecting that my domain would correctly read the above folder...

[HTML]
<VirtualHost *:80>  
ServerAdmin webmaster@localhost  
DocumentRoot /var/www/html
</VirtualHost>

<VirtualHost *:80>    
DocumentRoot /var/www/html/smf    
ServerName mysite.com    
ServerAlias *.mysite.com
</VirtualHost>
[/HTML]

as this did not work, I went and added the file **mysite.com.conf** to the directory **/etc/apache2/sites-available**

however, when I follow these instructions [https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04) and run **sudo apache2ctl configtest **I get:

[HTML]AH00112: Warning: DocumentRoot [/etc/apache2/var/www/html] does not existAH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this messageSyntax OK[/HTML]

Why am I getting a warning of a document root on etc/apache2? the var directory is at the same level as etc/

When trying to open the site, it shows:

**Not Found**

[COLOR=#000000][FONT=&amp]The requested URL was not found on this server.

Any help on this would be very much appreciated![/FONT][/COLOR]

---

### Post by davidsanchezvasquez on 2022-08-27
issue resolved... Settings.php from the SMF installation was still pointing to my old path www/html and not www/html/smf found this through the apache logs!

---

### Post by TheFu on 2022-08-27
I have to guess what you mean by "ubuntu 16", since that isn't a valid release name or number.  

Support for Ubuntu 16.04 ended in 2021.  Well passed time to move to a supported release.

Also, if this thread is solved, please use the Thread Tools button to mark it SOLVED so people don't waste their time.

---

### Post by davidsanchezvasquez on 2022-08-27
thread already marked as solved.

---

