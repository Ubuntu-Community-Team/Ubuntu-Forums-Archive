---
title: "Apache login auth"
date: 2012-12-01
forum: General Help
---

### Post by sucabuntu on 2012-12-01
Hello 
I'm trying to configure authentication for my apache web server

I created files .htaccess and .htpasswd in the directory /var/www

This is .htaccess

AuthName "Please log in"
AuthType Basic
AuthUserFile /var/www/.htpasswd
require user sucabuntu

This is .htpasswd

sucabuntu:$apr1$3o7y[CUT]ccZ3silh/0



Why login it's not working?

---

### Post by howefield on 2012-12-01
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2090098](http://ubuntuforums.org/showthread.php?t=2090098)

---

### Post by Elfy on 2012-12-01
Thread closed. Please do not post duplicates, it dilutes community effort.

---

