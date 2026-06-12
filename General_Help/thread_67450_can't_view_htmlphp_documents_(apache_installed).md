---
title: "can't view html/php documents (apache installed)"
date: 2005-09-20
forum: General Help
---

### Post by toshi on 2005-09-20
I've got a problem with the apache/php 5 thingie, I have installed libapache2-mod-php5, and fixed write/read permissions in var/www.
But when i visit 127.0.0.1/index.php, I just get the following:

Forbidden

You don't have permission to access /index.php on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.

anyone that knows what to do?

---

### Post by toshi on 2005-09-20
... and now I get a:


Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

---

