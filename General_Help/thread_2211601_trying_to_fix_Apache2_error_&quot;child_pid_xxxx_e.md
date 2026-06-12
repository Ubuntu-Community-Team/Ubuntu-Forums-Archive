---
title: "trying to fix Apache2 error &quot;child pid xxxx exit signal Segmentation fault&quot;"
date: 2014-03-16
forum: General Help
---

### Post by bphillips2 on 2014-03-16
I am trying to fix an issue I'm having and am running into a deadend.  I continue to get a Nginx 502 "bad gateway" error when loading a particular page.  I am using nginx to proxy to my apache server.  This is hosting a Zurmo (CRM) instance, among a few other things.  When I get the 502 error my apache2 error log has the following

> child pid 9135 exit signal Segmentation fault (11), possible coredump in /tmp/apache-coredumps

It does not create anything in the /tmp/apache-coredumps directory when this happens.

I ran a backtrace using [these]("http://stackoverflow.com/questions/7745578/notice-child-pid-xxxx-exit-signal-segmentation-fault-11-in-apache-error-lo") instructions and got the following

> justin@ubuntu:/var/log/apache2$ ps -ef|grep httpd
justin   10085  9604  0 18:49 pts/1    00:00:00 grep --color=auto httpd

> (gdb) attach 9604Attaching to process 9604
Reading symbols from /bin/bash...(no debugging symbols found)...done.
Reading symbols from /lib/x86_64-linux-gnu/libtinfo.so.5...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libtinfo.so.5
Reading symbols from /lib/x86_64-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libdl.so.2
Reading symbols from /lib/x86_64-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libc.so.6
Reading symbols from /lib64/ld-linux-x86-64.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnsl.so.1
Reading symbols from /lib/x86_64-linux-gnu/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/x86_64-linux-gnu/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/x86_64-linux-gnu/libnss_files.so.2
warning: no loadable sections found in added symbol-file system-supplied DSO at 0x7fffcfeee000
0x00007fbd5be60c8e in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) backtrace
#0  0x00007fbd5be60c8e in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x0000000000441419 in ?? ()
#2  0x000000000044255c in wait_for ()
#3  0x0000000000432c88 in execute_command_internal ()
#4  0x00000000004352fe in execute_command ()
#5  0x000000000041e31d in reader_loop ()
#6  0x000000000041ca87 in main ()

This is where my knowledge ends.  What do I do with this information? Am I even on the right track?

I'm using ubuntu 12.04, php 5.3.10

---

