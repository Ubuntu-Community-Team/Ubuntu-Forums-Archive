---
title: "ubuntu server 14 - downgrade php5.5 to php5.3"
date: 2014-11-22
forum: General Help
---

### Post by daemoncesar on 2014-11-22
I need to downgrade the php version 5.5 to 5.3.

What better way to do this?

---

### Post by daemoncesar on 2014-11-23
up

---

### Post by dragonfly41 on 2014-11-23
It might be better to run different versions of PHP and setup two virtualhosts for 5.3 and 5.5.

Here are a couple of articles explaining ...

[http://www.lornajane.net/posts/2014/running-multiple-versions-of-php](http://www.lornajane.net/posts/2014/running-multiple-versions-of-php)

[http://thejibe.com/blog/14/02/phpfarm](http://thejibe.com/blog/14/02/phpfarm)

Which application is asking you for a downgrade?

Currently I am testing one application which suggests that I downgrade from 5.5 but I refuse.

---

### Post by daemoncesar on 2014-11-23
A very old system that needs register_global = On

---

### Post by dragonfly41 on 2014-11-23
Setting aside the advice on this being a security risk .. here is one workaround I found... in a quick search 

[http://mrphp.com.au/blog/how-enable-register-globals-php-5](http://mrphp.com.au/blog/how-enable-register-globals-php-5)

---

### Post by daemoncesar on 2014-11-23
downgrade work !

how do I install the library ssh2 the old version of php ?

---

### Post by dragonfly41 on 2014-11-23
> downgrade work !

You need to expand a bit more.
Exactly what steps did you take from above posts to "downgrade"?

---

### Post by daemoncesar on 2014-11-23
I'm Running two versions of php+apache. 5.5 and 5.3.22.

but now I need to install ssh2 library, in the 5.3.22 version.

follow is reference:
```

https://gist.github.com/gmodarelli/5887778

```

---

### Post by dragonfly41 on 2014-11-23
I'm not too sure ..

But from here ...

[http://serverfault.com/questions/415458/php-error-cannot-find-openssls-evp-h](http://serverfault.com/questions/415458/php-error-cannot-find-openssls-evp-h)

> 
To build php-5.3 on Debian wheezy you need the following to fix this error.

    apt-get install [B]libssl-dev libsslcommon2-dev
[/B]
Then you need to configure with the following included

    ./configure --with-libdir=/lib/x86_64-linux-gnu ...



---

### Post by daemoncesar on 2014-11-23
--with-ssh2=/usr/lib/php5/20121212/ssh2.so \
--with-libdir=/usr/lib/php5/20121212/ssh2.so \

not work...

---

### Post by dragonfly41 on 2014-11-23
Have you tried installing ... libssh2-php

---

### Post by daemoncesar on 2014-11-23
this installed.

```

root@teste:/opt/phpfarm/src# locate ssh2.so
/usr/lib/php5/20121212/ssh2.so

```

---

### Post by dragonfly41 on 2014-11-23
phpseclib is suggested on some sites ... apparently works "out of the box"

[http://phpseclib.sourceforge.net/](http://phpseclib.sourceforge.net/)

try it.

Sorry I can't help further.

---

