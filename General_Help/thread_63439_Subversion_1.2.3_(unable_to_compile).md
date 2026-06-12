---
title: "Subversion 1.2.3 (unable to compile)"
date: 2005-09-07
forum: General Help
---

### Post by Taoism on 2005-09-07
I am a wee bit frustrated :)

I am trying to get Subversion to compile so I Eclipse will stop crashing with the Subclipse plugin from a javahl error.

I installled Berkeley DB 4.3.28.NC to make SVN happy, but it can't seem to see the libs of the DB, and I am getting somewhat tired at this point.

I exported the LD_LIBRARY_PATH:

```

youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 21:52:40 $ echo $LD_LIBRARY_PATH
:/usr/local/BerkeleyDB.4.3
youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 21:59:02 $

```

I even put the library path in d.so.conf (per the Berkeley instructions) [though I have no idea what the heck this file is for ;) ]
```

youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:02:03 $ cat /etc/ld.so.conf
/usr/X11R6/lib
/lib32
/usr/lib32
/usr/X11R6/lib32
/usr/local/apr/lib
/usr/local/BerkeleyDB.4.3/lib
youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:02:08 $

```

I am still getting:
```

checking for Berkeley DB... not found
configure: error: Berkeley DB not found.

```

As far as I can tell I have met all the dependencies to get to the point of compiling Subversion.

Here is the full dump from ./configure:
```

youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:05:10 $ sudo ./configure --with-openssl --with-berkeley-db=/usr/local/BerkeleyDB.4.3 --with-apr=/usr/local/apr
configure: Configuring Subversion 1.2.3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
configure: creating config.nice
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether ln -s works... yes
configure: Apache Portable Runtime (APR) library configuration
checking for APR... yes
checking APR version... 1.2.1
configure: Apache Portable Runtime Utility (APRUTIL) library configuration
checking for APR-util... reconfig
configuring package in apr-util now
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for working mkdir -p... yes
APR-util Version: 0.9.6
checking for chosen layout... apr-util
Applying apr-util hints file rules for x86_64-unknown-linux-gnu
checking for APR... yes
  setting CC to "gcc"
  setting CPP to "gcc -E"
  setting CFLAGS to " -g -O2 -pthread"
  setting CPPFLAGS to " -DLINUX=2 -D_REENTRANT -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -D_SVID_SOURCE -D_GNU_SOURCE"
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for ldap support...
checking gdbm.h usability... no
checking gdbm.h presence... no
checking for gdbm.h... no
checking for Berkeley DB 4.3 in /usr/local/BerkeleyDB.4.3...
checking db43/db.h usability... no
checking db43/db.h presence... no
checking for db43/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb-4.3... no
checking db43/db.h usability... no
checking db43/db.h presence... no
checking for db43/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb43... no
checking db43/db.h usability... no
checking db43/db.h presence... no
checking for db43/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb4... no
checking db43/db.h usability... no
checking db43/db.h presence... no
checking for db43/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb... no
checking for Berkeley DB 4.2 in /usr/local/BerkeleyDB.4.3...
checking db42/db.h usability... no
checking db42/db.h presence... no
checking for db42/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb-4.2... no
checking db42/db.h usability... no
checking db42/db.h presence... no
checking for db42/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb4... no
checking db42/db.h usability... no
checking db42/db.h presence... no
checking for db42/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb... no
checking for Berkeley DB 4.1 in /usr/local/BerkeleyDB.4.3...
checking db41/db.h usability... no
checking db41/db.h presence... no
checking for db41/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb-4.1... no
checking db41/db.h usability... no
checking db41/db.h presence... no
checking for db41/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb4... no
checking db41/db.h usability... no
checking db41/db.h presence... no
checking for db41/db.h... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb... no
checking for Berkeley DB 4.0 in /usr/local/BerkeleyDB.4.3...
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb-4.0... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb4... no
checking db4/db.h usability... no
checking db4/db.h presence... no
checking for db4/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb... no
checking for Berkeley DB 3 in /usr/local/BerkeleyDB.4.3...
checking db3/db.h usability... no
checking db3/db.h presence... no
checking for db3/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb3... no
checking db3/db.h usability... no
checking db3/db.h presence... no
checking for db3/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for -ldb... no
checking for Berkeley DB 2 in /usr/local/BerkeleyDB.4.3...
checking db2/db.h usability... no
checking db2/db.h presence... no
checking for db2/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for db_open in -ldb2... no
checking db2/db.h usability... no
checking db2/db.h presence... no
checking for db2/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for db_open in -ldb... no
checking for Berkeley DB 1.0.0 in /usr/local/BerkeleyDB.4.3...
checking db1/db.h usability... no
checking db1/db.h presence... no
checking for db1/db.h... no
checking db.h usability... yes
checking db.h presence... yes
checking for db.h... yes
checking for dbopen in -ldb1... no
checking for Berkeley DB 1 in /usr/local/BerkeleyDB.4.3...
checking db_185.h usability... yes
checking db_185.h presence... yes
checking for db_185.h... yes
checking for dbopen in -ldb... no
checking for Berkeley DB... not found
configure: error: Berkeley DB not found.
configure failed for apr-util
youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:05:36 $

```

And the Berkeley lib directory (as installed/created by Berkeley DB):
```

youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:05:36 $ ls -l /usr/local/BerkeleyDB.4.3/lib/
total 3804
-rw-r--r--  1 root root 1480668 2005-09-07 21:39 libdb-4.3.a
-rw-r--r--  1 root root     810 2005-09-07 21:38 libdb-4.3.la
-rwxr-xr-x  1 root root  909904 2005-09-07 21:38 libdb-4.3.so
lrwxrwxrwx  1 root root      12 2005-09-07 21:39 libdb-4.so -> libdb-4.3.so
-rw-r--r--  1 root root 1480668 2005-09-07 21:39 libdb.a
lrwxrwxrwx  1 root root      12 2005-09-07 21:39 libdb.so -> libdb-4.3.so
youngka@quidditch:~/downloads/subversion-1.2.3.tar_FILES/subversion-1.2.3
Wed Sep 07 22:08:44 $

```

So is the make file for Subversion just not looking for the right db files?

If anyone can give me some insight into this problem I would really appreciate it.

Cheers,
Keith.

---

### Post by crouton on 2005-10-17
You don't need to use the BerkelyDB's, you can use the FSFS flat filesystem, which tends to work better in many respects.  Ignore the BerkelyDB issues and keep forging ahead, see what happens.

---

