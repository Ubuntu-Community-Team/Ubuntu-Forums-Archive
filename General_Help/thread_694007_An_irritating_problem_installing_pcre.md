---
title: "An irritating problem installing pcre"
date: 2008-02-11
forum: General Help
---

### Post by LEDZO on 2008-02-11
I was trying to install pcre and i got as far as installing it when it gave me this error message at the very end. I tried to paste a little before the error just in case. I don't understand how to relink it or even what that means
```


libpcrecpp.so /home/profoak/Desktop/pcre-7.6/.libs/libpcre.so 
creating pcre_stringpiece_unittest
make[1]: Leaving directory `/home/profoak/Desktop/pcre-7.6'
profoak@ttt:~/Desktop/pcre-7.6$ make install
make[1]: Entering directory `/home/profoak/Desktop/pcre-7.6'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libpcre.la' '/usr/local/lib/libpcre.la'
/usr/bin/install -c .libs/libpcre.so.0.0.1 /usr/local/lib/libpcre.so.0.0.1
/usr/bin/install: cannot create regular file `/usr/local/lib/libpcre.so.0.0.1': Permission denied
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libpcreposix.la' '/usr/local/lib/libpcreposix.la'
libtool: install: warning: relinking `libpcreposix.la'
(cd /home/profoak/Desktop/pcre-7.6; /bin/bash ./libtool  --tag=CC --mode=relink gcc -O2 -version-info 0:0:0 -o libpcreposix.la -rpath /usr/local/lib pcreposix.lo libpcre.la )  
gcc -shared  .libs/pcreposix.o  -L/usr/local/lib -lpcre  -Wl,-soname -Wl,libpcreposix.so.0 -o .libs/libpcreposix.so.0.0.0
/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
libtool: install: error: relink `libpcreposix.la' with the above command before installing it
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libpcrecpp.la' '/usr/local/lib/libpcrecpp.la'
libtool: install: warning: relinking `libpcrecpp.la'
(cd /home/profoak/Desktop/pcre-7.6; /bin/bash ./libtool  --tag=CXX --mode=relink g++ -O2 -version-info 0:0:0 -o libpcrecpp.la -rpath /usr/local/lib pcrecpp.lo pcre_scanner.lo pcre_stringpiece.lo libpcre.la )  
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.3/crtbeginS.o  .libs/pcrecpp.o .libs/pcre_scanner.o .libs/pcre_stringpiece.o  -L/usr/local/lib -lpcre -L/usr/lib/gcc/i486-linux-gnu/4.1.3 -L/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.1.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libpcrecpp.so.0 -o .libs/libpcrecpp.so.0.0.0
/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
libtool: install: error: relink `libpcrecpp.la' with the above command before installing it
make[1]: *** [install-libLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/profoak/Desktop/pcre-7.6'
make: *** [install-am] Error 2
profoak@277:~/Desktop/pcre-7.6$ 


```

---

