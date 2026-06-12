---
title: "Trouble Locating PHP.INI"
date: 2007-09-12
forum: General Help
---

### Post by snick512 on 2007-09-12
Uh... i have everything setup, php/apache.

i go to /var/php5 but no files show.

Im trying to setup a web interface for ktorrent, and cant find the php.ini

where is the php.ini file?

---

### Post by Koybe on 2007-09-12
If I remember well it should be on ```
/etc/php5/apache2/php.ini
``` could depends on version you are using.

Anyway you ccan always look after a file...
```
sudo find /etc -name php.ini
```
... and found the answer. ;)

---

### Post by snick512 on 2007-09-12
"HTTP/1.1 Internal Server Error
PHP executable error"

I guess i was aim'ing for the wrong file > . < idk why i was thinking ini

where can i find the executable?


sorry :( lol

---

### Post by RiTarDid on 2008-01-18
i used /usr/bin/php but it wouldn't login to webgui...then i used /usr/bin/php5....i'lll let you know how that goes

---

