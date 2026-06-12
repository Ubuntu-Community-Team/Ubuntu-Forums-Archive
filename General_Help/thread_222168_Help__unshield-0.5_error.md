---
title: "Help  unshield-0.5 error"
date: 2006-07-24
forum: General Help
---

### Post by cc500 on 2006-07-24
I was trying to install unshield-0.5 using /.configure which worked fine, but then I tried to make it and it gave me some errors and was wondering if anyone else has experienced problems like this. Here's the log:

chris@chris-desktop:~/Desktop/unshield-0.5$ sudo make
Password:
Making all in lib
make[1]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
make  all-recursive
make[2]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
Making all in md5
make[3]: Entering directory `/home/chris/Desktop/unshield-0.5/lib/md5'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib/md5'
Making all in .
make[3]: Entering directory `/home/chris/Desktop/unshield-0.5/lib'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -ansi -Wall -Wsign-compare -Wno-long-long -Werror -g -O2  -I.. -g -O2 -MT file.lo -MD -MP -MF ".deps/file.Tpo" \
          -c -o file.lo `test -f 'file.c' || echo './'`file.c; \
        then mv -f ".deps/file.Tpo" ".deps/file.Plo"; \
        else rm -f ".deps/file.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -ansi -Wall -Wsign-compare -Wno-long-long -Werror -g -O2 -I.. -g -O2 -MT file.lo -MD -MP -MF .deps/file.Tpo -c file.c  -fPIC -DPIC -o .libs/file.o
file.c:11:18: error: zlib.h: No such file or directory
file.c:209: error: syntax error before '*' token
file.c: In function 'unshield_uncompress':
file.c:211: error: 'z_stream' undeclared (first use in this function)
file.c:211: error: (Each undeclared identifier is reported only once
file.c:211: error: for each function it appears in.)
file.c:211: error: syntax error before 'stream'
file.c:214: error: 'stream' undeclared (first use in this function)
file.c:214: error: 'source' undeclared (first use in this function)
file.c:215: error: 'uInt' undeclared (first use in this function)
file.c:215: error: syntax error before 'sourceLen'
file.c:217: error: 'dest' undeclared (first use in this function)
file.c:218: error: 'destLen' undeclared (first use in this function)
file.c:220: error: 'alloc_func' undeclared (first use in this function)
file.c:220: error: syntax error before numeric constant
file.c:221: error: 'free_func' undeclared (first use in this function)
file.c:221: error: syntax error before numeric constant
cc1: warnings being treated as errors
file.c:224: warning: implicit declaration of function 'inflateInit2'
file.c:224: error: 'MAX_WBITS' undeclared (first use in this function)
file.c:225: error: 'Z_OK' undeclared (first use in this function)
file.c:227: warning: implicit declaration of function 'inflate'
file.c:227: error: 'Z_FINISH' undeclared (first use in this function)
file.c:228: error: 'Z_STREAM_END' undeclared (first use in this function)
file.c:229: warning: implicit declaration of function 'inflateEnd'
file.c: In function 'unshield_file_save':
file.c:565: error: 'uLong' undeclared (first use in this function)
file.c:565: error: syntax error before 'total_written'
file.c:625: error: syntax error before 'bytes_to_write'
file.c:653: error: 'bytes_to_write' undeclared (first use in this function)
file.c:655: error: 'Z_OK' undeclared (first use in this function)
file.c:692: error: 'total_written' undeclared (first use in this function)
make[3]: *** [file.lo] Error 1
make[3]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/chris/Desktop/unshield-0.5/lib'
make: *** [all-recursive] Error 1

---

