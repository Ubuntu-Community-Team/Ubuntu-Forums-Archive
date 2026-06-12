---
title: "amarok crashes and i get this messgae.."
date: 2007-05-15
forum: General Help
---

### Post by zeltak on 2007-05-15
hi guys

I had some major problems with my kubuntu and now it seems that things are back to normal. one thing thst still drives me nuts is amarok keeps crashing all the time. i get this message when i run it from the command line:

terminate called after throwing an instance of '__gnu_cxx::recursive_init'
  what():  N9__gnu_cxx14recursive_initE


does any one know what it means?

thx 

Zeltak

---

### Post by pianoboy3333 on 2007-05-15
I'm not sure... you may want to try compiling amarok from source, or reinstalling it:

sudo apt-get install --reinstall <package>

---

### Post by zeltak on 2007-05-16
hi 

thx for the answer. ive tried re-installing but unfortunately it didn't work 

id be happy with any other suggestions to try

zeltak

---

### Post by zeltak on 2007-05-21
hi

Just to add that i get this message when i start amarok:

======== DEBUG INFORMATION  =======
Version:    1.4.5
Engine:     xine-engine
Build date: Apr  4 2007
CC version: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
KDElibs:    3.5.6
Qt:         3.3.7
TagLib:     1.4.0
CPU count:  2
NDEBUG:     true
==== file `which amarokapp` =======
/usr/bin/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1253640496 (LWP 18055)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6b710b3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d3a1 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb66eedf0 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb66f0641 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb68f2270 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#8  0xb68efca5 in ?? () from /usr/lib/libstdc++.so.6
#9  0xb68efce2 in std::terminate () from /usr/lib/libstdc++.so.6
#10 0xb68efe1a in __cxa_throw () from /usr/lib/libstdc++.so.6
#11 0xb68effad in ?? () from /usr/lib/libstdc++.so.6
#12 0xb68f00c9 in __cxa_guard_acquire () from /usr/lib/libstdc++.so.6
#13 0xb7c1f2be in MountPointManager::instance () from /usr/lib/libamarok.so.0
#14 0xb7b254f7 in QueryBuilder::addMatch () from /usr/lib/libamarok.so.0
#15 0xb7b276b1 in CollectionDB::getSongRating () from /usr/lib/libamarok.so.0
#16 0xb7d94753 in Amarok::DcopPlayerHandler::rating ()
   from /usr/lib/libamarok.so.0
#17 0xb7da18a8 in AmarokPlayerInterface::process ()
   from /usr/lib/libamarok.so.0
#18 0xb5e520c7 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
#19 0xb5e53424 in ?? () from /usr/lib/libDCOP.so.4
#20 0x080bfdb8 in ?? ()
#21 0xbfef8a64 in ?? ()
#22 0xbfef8a5c in ?? ()
#23 0xbfef8a54 in ?? ()
#24 0xbfef8a4c in ?? ()
#25 0xbfef8a44 in ?? ()
#26 0xbfef8a3c in ?? ()
#27 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6b710b3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x0804d3a1 in Amarok::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb66eedf0 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb66f0641 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb68f2270 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
No symbol table info available.
#8  0xb68efca5 in ?? () from /usr/lib/libstdc++.so.6
No symbol table info available.
#9  0xb68efce2 in std::terminate () from /usr/lib/libstdc++.so.6
No symbol table info available.
#10 0xb68efe1a in __cxa_throw () from /usr/lib/libstdc++.so.6
No symbol table info available.
#11 0xb68effad in ?? () from /usr/lib/libstdc++.so.6
No symbol table info available.
#12 0xb68f00c9 in __cxa_guard_acquire () from /usr/lib/libstdc++.so.6
No symbol table info available.
#13 0xb7c1f2be in MountPointManager::instance () from /usr/lib/libamarok.so.0
No symbol table info available.
#14 0xb7b254f7 in QueryBuilder::addMatch () from /usr/lib/libamarok.so.0
No symbol table info available.
#15 0xb7b276b1 in CollectionDB::getSongRating () from /usr/lib/libamarok.so.0
No symbol table info available.
#16 0xb7d94753 in Amarok::DcopPlayerHandler::rating ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#17 0xb7da18a8 in AmarokPlayerInterface::process ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#18 0xb5e520c7 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
No symbol table info available.
#19 0xb5e53424 in ?? () from /usr/lib/libDCOP.so.4
No symbol table info available.
#20 0x080bfdb8 in ?? ()
No symbol table info available.
#21 0xbfef8a64 in ?? ()
No symbol table info available.
#22 0xbfef8a5c in ?? ()
No symbol table info available.
#23 0xbfef8a54 in ?? ()
No symbol table info available.
#24 0xbfef8a4c in ?? ()
No symbol table info available.
#25 0xbfef8a44 in ?? ()
No symbol table info available.
#26 0xbfef8a3c in ?? ()
No symbol table info available.
#27 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 1 (Thread -1253640496 (LWP 18055)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6b710b3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d3a1 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb66eedf0 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb66f0641 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb68f2270 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#8  0xb68efca5 in ?? () from /usr/lib/libstdc++.so.6
#9  0xb68efce2 in std::terminate () from /usr/lib/libstdc++.so.6
#10 0xb68efe1a in __cxa_throw () from /usr/lib/libstdc++.so.6
#11 0xb68effad in ?? () from /usr/lib/libstdc++.so.6
#12 0xb68f00c9 in __cxa_guard_acquire () from /usr/lib/libstdc++.so.6
#13 0xb7c1f2be in MountPointManager::instance () from /usr/lib/libamarok.so.0
#14 0xb7b254f7 in QueryBuilder::addMatch () from /usr/lib/libamarok.so.0
#15 0xb7b276b1 in CollectionDB::getSongRating () from /usr/lib/libamarok.so.0
#16 0xb7d94753 in Amarok::DcopPlayerHandler::rating ()
   from /usr/lib/libamarok.so.0
#17 0xb7da18a8 in AmarokPlayerInterface::process ()
   from /usr/lib/libamarok.so.0
#18 0xb5e520c7 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
#19 0xb5e53424 in ?? () from /usr/lib/libDCOP.so.4
#20 0x080bfdb8 in ?? ()
#21 0xbfef8a64 in ?? ()
#22 0xbfef8a5c in ?? ()
#23 0xbfef8a54 in ?? ()
#24 0xbfef8a4c in ?? ()
#25 0xbfef8a44 in ?? ()
#26 0xbfef8a3c in ?? ()
#27 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================

any ideas anyone?

thx

Zeltak

---

### Post by kernel tom on 2007-05-29
Now technically this is re-installing it but i had a different error message...

my terminal output said something like this 
"Amarok is taking a long time to load... Is something wrong?"
which I found quite comical but not helpful

I reinstalled it via the terminal like this:

sudo apt-get remove amarok
sudo apt-get autoremove
sudo apt-get install amarok

rebooted and it worked fine,
maybe that'll help

---

### Post by bleaked on 2007-06-18
I had been experiencing this same problem with amarok over the past few days.  After searching around I finally found an answer on kubuntuforums.net suggesting that I remove the ~/.xine folder, since it was being corrupted for whatever reason.

So a quick removal of the ~/.xine directory should fix your problem with amarok:
 ```
$ rm -rf ~/.xine
```

---

