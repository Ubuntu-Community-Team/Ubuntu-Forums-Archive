---
title: "Cannot build courier with deb source packages"
date: 2006-10-13
forum: General Help
---

### Post by chrish01 on 2006-10-13
Courier does not seem to be building on my dapper lts server. I'm getting the source from `apt-get source courier` and building with `./debian/rules binary`. It dies when working in the ./webmail folder. I did `apt-get build-dep courier` before hand.

..
make[2]: Entering directory `/home/chris/courier-0.47/webmail'
gcc  -g -O2 -Wall -I.. -I./..  -lcrypt -o sqwebmail  sqwebmaild.o ../cgi/libcgi.a -lcrypt 
../cgi/libcgi.a(cginocache.o): In function `cginocache':/home/chris/courier-0.47/cgi/cginocache.c:18: undefined reference to `FCGI_printf'
:/home/chris/courier-0.47/cgi/cginocache.c:19: undefined reference to `FCGI_printf'
../cgi/libcgi.a(cginocache.o): In function `cginocache_msie':/home/chris/courier-0.47/cgi/cginocache.c:26: undefined reference to `FCGI_printf'
:/home/chris/courier-0.47/cgi/cginocache.c:27: undefined reference to `FCGI_printf'
collect2: ld returned 1 exit status
make[2]: *** [sqwebmail] Error 1
make[2]: Leaving directory `/home/chris/courier-0.47/webmail'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/courier-0.47/webmail'
make: *** [all] Error 2

TIA

-- Christian

---

