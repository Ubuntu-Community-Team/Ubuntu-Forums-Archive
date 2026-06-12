---
title: "[SOLVED] phpmyadmin error: The configuration file now needs a secret......"
date: 2007-11-23
forum: General Help
---

### Post by bobleny on 2007-11-23
OK, so I have an issue with phpmyadmin.

I can't actually log into the phpmyadmin panel, but I do have access to mysql via PHP.

The error I get reads:
The configuration file now needs a secret passphrase (blowfish_secret).

I looked online and the solution is simple, edit the config.inc.php file the line:
$cfg['blowfish_secret'] = '';

should equal a password. Something like:
$cfg['blowfish_secret'] = 'holla';
----------------------------

Anyways, this isn't my issue. When I check the file, the line already read:
$cfg['blowfish_secret'] = 'JFxf53DW3HtalwEkkusnEmjuQ';


I did some file searching and I found many different config.inc.php files around my computer. Three of which had this exact line in it:
$cfg['blowfish_secret'] = 'JFxf53DW3HtalwEkkusnEmjuQ';

The files where in these locations:
/var/lib/phpmyadmin/
/etc/phpmyadmin/
/usr/share/phpmyadmin/config/
------------------------


I don't know what else to do. I would sort of like access to phpmyadmin. It is a very nice program...

Can anyone please help me?

Thanks!

---

### Post by bobleny on 2007-11-26
I was thinking about it and I thought maybe it is a permissions issue. So, I searched the computer for any files owned by www-data and changed the the owner to me.

Now it works again with no problems...

Thanks for everybody's... err... Umm. Well thanks for.... OK, bye.

---

### Post by Railsbuntu on 2008-01-24
Hi, I have this problem too, but there is a secret passphrase in config.inc.php

This happened when installing nginx and redirecting php to a fastcgi server spawned by the program spawn-fcgi that comes with lighttpd.

What is that passphrase issue?

---

### Post by ddoxey on 2008-03-10
I'm going to second bobleny's solution.

I've been seeing this for quite some time and I've just been resorting to CLI mysql because I've been too lazy to resolve it.

Speaking of lazy, for some reason of convenience I changed my Apache configuration to run as me. This is what caused phpmyadmin to go belly up.

The exact fix:
sudo chown -R ddoxey /var/lib/phpmyadmin/

Thanks bobleny.

---

### Post by mafitzpatrick on 2008-03-24
Responding to a very old thread, but the actual solution is:

Open /var/lib/phpmyadmin/blowfish_secret.inc.php and you'll find the 'blowfish' config line.
Copy that and paste it into the file at /etc/phpmyadmin/blowfish_secret.inc.php

And it will work.

---

### Post by dsiembab on 2008-04-16
didn't solve it for me so instead I went into my /var/lib/phpmyadmin/blowfish_secret.inc.php and copied the ```
$cfg['blowfish_secret'] = 'your hash here';
```
and pasted at the bottom of /etc/phpmyadmin/config.inc.php
that seemed to work for me. I didn't have a /etc/phpmyadmin/blowfish_secret.inc.php
of course being a lazy man I used sudo nautilus in terminal

---

