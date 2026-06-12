---
title: "Apache, on my LAN"
date: 2005-10-04
forum: General Help
---

### Post by xmastree on 2005-10-04
Hi, I've installed apache on one computer on my LAN.
From that computer, if I browse to [http://127.0.0.1](http://127.0.0.1) I get the standard greeting page stored at /var/www/index.html
However, if I use a different computer on the LAN, I can't connect, it just times out.
Do I need to tell the apache unit to allow connections from 192.168.1.* or something? I've looked at /etc/apache/httpd.conf and I tried putting ```
Allow from 192.168.1.*
``` in the <directory> section but that didn't help.
I can ping the apache unit from different machines, but can't connect to it with a web browser.
What's the secret?

Edit: Fixed it. Seems I had the firewall blocking all incoming connections...

---

