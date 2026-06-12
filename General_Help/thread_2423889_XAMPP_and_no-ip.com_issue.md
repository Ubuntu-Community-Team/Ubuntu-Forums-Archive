---
title: "XAMPP and no-ip.com issue"
date: 2019-07-31
forum: General Help
---

### Post by jurito on 2019-07-31
Hello,
I have a bit of a problem with XAMPP on Ubuntu and ddns (no-ip.com), it's probably something stupid but i can't sort it out.


I have setup XAMPP, a ddns account, port forwarding and everything works fine. The webserver is reached via the *.ddns.net address.


BUT, if I enable my vhosts file ( uncommenting *#Include etc/extra/httpd-vhosts.conf in httpd.conf *) in which the very first is localhost:

```
<VirtualHost *:80>
  DocumentRoot "/opt/lampp/htdocs"
  DirectoryIndex index.php
  ServerName localhost


  <Directory "/opt/lampp/htdocs">
  Options All
  AllowOverride All
  Require all granted
  </Directory>
</VirtualHost>

```

..everything works locally but ddns doesn't open anything anymore. To clarify, I would use my other vhosts locally for dev purposes, while the ddns url should show localhost root.


Anyone sees some blatant error in my setup that i missed? 

TIA

---

