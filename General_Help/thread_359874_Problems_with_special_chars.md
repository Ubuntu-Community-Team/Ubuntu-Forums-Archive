---
title: "Problems with special chars"
date: 2007-02-12
forum: General Help
---

### Post by bolbit on 2007-02-12
Hi Forum,

I have problem with special chars.
I posted my problem in the german forum [1], but i got no answer i hope that here is someone helping me with my problem.

When i download files from the internet or files from external devices like CD, Pictures on SD-Card the special chars are interpreted incorrectly.

For example i download a php file i find somithing like 
> 
...
define('_MSDELAY', 'Verz&#65533;erung');
... 
 
in it.

In the phpmyadmin i installed with apt i find a text like 
> 
Ihre Konfigurationsdatei enth&#65533;lt Einstellungen (Benutzer "root" ohne Passwort), welche denen des MySQL-Standardbenutzers entsprechen. Wird Ihr MySQL-Server mit diesen Einstellungen betrieben, so k&#65533;nnen Unbefugte leicht von au&#65533;en auf ihn zugreifen. Sie sollten diese Sicherheitsl&#65533;cke unbedingt schlie&#65533;en! 


but when i type
> 
touche ööö.äää

i find a file named ööö.äää

so special chars makes only problems when they come from outside.

Has anyone a idea how to fix this?

Thanks


[1] [http://forum.ubuntuusers.de/topic/72442/?highlight=](http://forum.ubuntuusers.de/topic/72442/?highlight=)

---

### Post by bolbit on 2007-02-20
*push*

has still nobody an idea?

---

