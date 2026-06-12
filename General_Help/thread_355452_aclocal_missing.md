---
title: "aclocal missing"
date: 2007-02-07
forum: General Help
---

### Post by haylocki on 2007-02-07
Hi, I have just spent the whole day trying to compile Avidemx svn on my system.

I kept getting the error :

*** Creating aclocal.m4
./admin/cvs.sh: 601: aclocal: not found
make[1]: *** [cvs] Error 1

whilst trying to configure the software.

I tried uninstalling and reinstallng all the usual dev libraries and tools to no avail.:( 

The solution in the end was :

/usr/bin/ only contained a file called "aclocal-1.9"

[B]cp /usr/bin/aclocal-1.9  /usr/bin/aclocal
[/B]
and Tada!! :) the software can now find aclocal.

Don't know if this is the right thing to do, but after a whole day googling for a solution and finding nowt, I am just happy it works.

So I am posting this thread in case someone else has the same problem with aclocal missing.

Cheers, Ian

---

