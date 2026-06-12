---
title: "Apache2 - tweak configuration help"
date: 2005-08-28
forum: General Help
---

### Post by dbeckham32 on 2005-08-28
Okay, I've managed to get Apache2, PHP and MySQL installed and working correctly. But Apache2 is using the default configuration and I'd like to change my docroot so I can access URLs outside of /var/www/ (it's a root-owned directory, after all).

Can someone please post their httpd.conf file so I can see a sample user configuration? Can't seem to locate an Apache2 newbie guide on the Net.

Specifically, I'd like to:
- access HTML docs from my home directory (/home/username/web)
- set up SSI to parse above location

Anyone? Please and thanks!

---

### Post by nozey on 2005-08-28
U can change your document root at:

/etc/apache2/sites-enabled/000-default

---

