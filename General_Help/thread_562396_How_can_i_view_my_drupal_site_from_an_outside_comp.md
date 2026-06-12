---
title: "How can i view my drupal site from an outside computer?"
date: 2007-09-28
forum: General Help
---

### Post by Uottawaess on 2007-09-28
Currently whenever i type in the IP of the webserver im hosting it on it just gives me the apache page

IT WORKS!

but so far i havent seen any guides on how to direct it towards my www/drupal/sites/sitename
instead

any help :( ??


im using my own webserver

OS = feisty faun version 7.04
Drupal 5.1
Apache 2



I CAN access [http://localhost/drupal/index.php](http://localhost/drupal/index.php) 
and ive already made my administrator account and setup my database

---

### Post by trippinnik on 2007-09-29
check here: [http://httpd.apache.org/docs/2.0/configuring.html](http://httpd.apache.org/docs/2.0/configuring.html)
Apache project has some great documentation.  basically you'll edit a configuration file to change the root directory for Apache.  I don't remember which one though...

---

