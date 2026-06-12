---
title: "ktorrent-2.2.2.tar.gz"
date: 2007-11-15
forum: General Help
---

### Post by aek21 on 2007-11-15
hello


i downloaded ktorrent-2.2.2.tar.gz and tried to compile.

after ./configure it ended like this:

```
----------------------------------------------------------
KTorrent ERROR:
KTorrent requires gmp (http://www.swox.com/gmp)
----------------------------------------------------------


Good - your configure finished. Start make now


```

then i tried make and at the end it returned

```
../../libktorrent/mse/bigint.h:26:17: error: gmp.h: No such file or directory
../../libktorrent/mse/bigint.h:93: error: 'mpz_t' does not name a type
make[4]: *** [peermanager.lo] Error 1
make[4]: Leaving directory `/home/......./ktorrent-2.2.2/libktorrent/torrent'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/......./ktorrent-2.2.2/libktorrent'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/......./ktorrent-2.2.2/libktorrent'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/......./ktorrent-2.2.2'
make: *** [all] Error 2

```

any idea what to do to fix this?

---

### Post by hvbakel on 2007-11-15
Yes, you need to install libgmp3-dev. You can do that from the terminal by issuing the command

```
sudo apt-get install libgmp3-dev
```

What usually helps in these cases is to use adept or synaptic to search for the name of the missing package that is mentioned by the configure script and then install the '-dev' version of the matching package. On another note, ktorrent-2.2.3 was released yesterday so you might try compiling that instead.

---

