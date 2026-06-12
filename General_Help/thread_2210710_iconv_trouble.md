---
title: "iconv trouble"
date: 2014-03-12
forum: General Help
---

### Post by shestero on 2014-03-12
In my Ubuntu 12.04 LTS trying avoid the bug in iconv utility [https://sourceware.org/bugzilla/show_bug.cgi?id=6050](https://sourceware.org/bugzilla/show_bug.cgi?id=6050) that affected me
I manually installed GNU Libiconv from here [https://www.gnu.org/software/libiconv/](https://www.gnu.org/software/libiconv/)  ( using ./configure; make; sudo make install ).
Then iconv works no more at all:
$ iconv
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory

What should I do now to
1. restore my old iconv utility back (may be reinstall some packages?)
2. get a new iconv utility without the bug or another utility with the same functions without the bug.

---

### Post by dargaud2 on 2014-03-12
Search for libiconv.so in either /lib or you compilation directory. Is the newly compiled version in the right place ?

Also, why can't you use a file as an intermediate step ? Instead of "someprog | iconv", run "someprog >/tmp/toconv; iconv /tmp/toconv"

---

### Post by shestero on 2014-03-12
I don't know where the "right place" is.
Content of my /usr/local/lib/ directory:
total 2716
-rw-r--r-- 1 root root      212 Mar 12 16:45 charset.alias
-rw-r--r-- 1 root root    42304 Mar 12 16:45 libcharset.a
-rw-r--r-- 1 root root      936 Mar 12 16:45 libcharset.la
lrwxrwxrwx 1 root root       19 Mar 12 16:45 libcharset.so -> libcharset.so.1.0.0
lrwxrwxrwx 1 root root       19 Mar 12 16:45 libcharset.so.1 -> libcharset.so.1.0.0
-rw-r--r-- 1 root root    36914 Mar 12 16:45 libcharset.so.1.0.0
-rw-r--r-- 1 root root      912 Mar 12 16:45 libiconv.la
lrwxrwxrwx 1 root root       17 Mar 12 16:45 libiconv.so -> libiconv.so.2.5.1
lrwxrwxrwx 1 root root       17 Mar 12 16:45 libiconv.so.2 -> libiconv.so.2.5.1
-rw-r--r-- 1 root root  1340511 Mar 12 16:45 libiconv.so.2.5.1
-rw-r--r-- 1 root root  1315636 Mar 12 16:45 preloadable_libiconv.so
drwxrwsr-x 4 root staff    4096 Mar  4 22:47 python2.7
drwxrwsr-x 3 root staff    4096 Nov  1 01:57 python3.2
drwxr-xr-x 3 root root     4096 Nov 28 08:51 site_ruby

Looks like there are no more libiconv.so.2 files in my system.

>[COLOR=#000000]Also, why can't you use a file as an intermediate step ? Instead of "someprog | iconv", run "someprog >/tmp/toconv; iconv /tmp/toconv"
Because:
1. data may be >>10 Gb. This overflow the RAM with buggy iconv. I found it so long as two years ago and write my own iconv, see here: [/COLOR]http://netdbview.com/myiconv/
[COLOR=#000000]This code do my task well. Now (unfortunately) I tried to solve problem "in right way" (with "standard" tools).
2. data comes and receives slowly and should be processed on the flow in order to spare time. If you read all data then send all data it double the time.

[/COLOR]

---

### Post by shestero on 2014-03-12
Looks like I've solve my problem reinstalling reconfigured GNU libiconv with option:
./configure --prefix=/usr/

---

### Post by steeldriver on 2014-03-12
Looks like all it needs is to run ldconfig manually:

```

$ ldd $(which iconv)
        linux-gate.so.1 =>  (0xb77b1000)
        /usr/local/lib/preloadable_libiconv.so (0xb76cc000)
[COLOR=#ff0000]**        libiconv.so.2 => not found**[/COLOR]
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb74f7000)
        /lib/ld-linux.so.2 (0xb77b2000)

**$ sudo ldconfig -v**
$ 
$ ldd $(which iconv)
        linux-gate.so.1 =>  (0xb77b4000)
        /usr/local/lib/preloadable_libiconv.so (0xb76cf000)
[COLOR=#0000ff]**        libiconv.so.2 => /usr/local/lib/libiconv.so.2 (0xb75c1000)**[/COLOR]
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7416000)
        /lib/ld-linux.so.2 (0xb77b5000)

```

---

