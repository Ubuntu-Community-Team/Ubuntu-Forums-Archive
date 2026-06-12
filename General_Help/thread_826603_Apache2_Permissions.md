---
title: "Apache2 Permissions"
date: 2008-06-12
forum: General Help
---

### Post by kamasheto on 2008-06-12
Hey,

I've been trying to fix my localhost for two days now with no success. I've installed apache2 and it's running fine except for the permissions. My user cannot edit any of the files in there, I can write in there, but cannot edit.

I've tried all the solutions proposed in [this thread](http://ubuntuforums.org/showthread.php?t=17457&). I've tried to chgrp -R /var/www to www-data then added my user to that group.

Any suggestions? Thanks in advance.

---

### Post by kamasheto on 2008-06-12
Funny, I solve this on my own the moment I ask for help.

Anyway, just for the record here's how I solved this problem:

$ mkdir ~/www
$ sudo gedit /etc/apache2/sites-enabled/000-default
- Change the two instances of /var/www/ to /home/yourusername/www/
- Save and close
$ sudo apache2ctl restart

This probably isn't the best solution especially for servers, but it seems a not-so-bad solution if you're the only user that uses Ubuntu.

Future suggestions still welcome. Thanks again.

---

### Post by egamal on 2008-11-21
well, I do changed the document root once I installed Apache ages ago, but is there anyway to let apache has the permission to make directories or touch files ..
it always give me the "permission denied" error while trying to touch files using PHP scripts ..

Any idea how can I fix it ?

---

