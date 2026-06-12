---
title: "GPG error: http://www.openprinting.org lsb3.1"
date: 2014-01-01
forum: General Help
---

### Post by chox on 2014-01-01
Hi, 

Can anyone help me with this?
GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.1 Release: The following signatures were invalid: BADSIG 7A4B44C2D2A2203E OpenPrinting (OpenPrinting Test Key) <webmaster@openprinting.org>

I tried this: [http://ubuntuforums.org/showthread.php?t=2042929&p=12174672#post12174672](http://ubuntuforums.org/showthread.php?t=2042929&p=12174672#post12174672)
but it seems like it doesn't help or i might doing it wrong. 

Any updates if this problem got solved?

Thanks!

---

### Post by chox on 2014-01-01
It worked now... I think I didn't read too much. My bad! 

So, based on this forum: [http://ubuntuforums.org/showthread.php?t=2042929&p=12174672#post12174672](http://ubuntuforums.org/showthread.php?t=2042929&p=12174672#post12174672)
What I did is, I edit the repo entry in /etc/apt/sources.list for openprinting.org and changed:

deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint

to:

deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main

Works fine now! 

Hope this will help you too.. :)

---

