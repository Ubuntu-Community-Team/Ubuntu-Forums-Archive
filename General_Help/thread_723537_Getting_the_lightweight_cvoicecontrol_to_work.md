---
title: "Getting the lightweight cvoicecontrol to work ?"
date: 2008-03-13
forum: General Help
---

### Post by frenchn00b on 2008-03-13
Hello

I just tried the program cvoicecontrol, to control pc with voice.
I am n00b and got this:

voice.sh
Code:

#!/usr/bin/tcsh

  cvoicecontrol --once frenchn00b.cvc
  set result = $status

  if ($result == "-1") then
    echo "Error!"
  else if ($result == "0") then
    echo "You said yes"
  else if ($result == "1")
    echo "You said no"
  endif

  exit

Code:

sh voice.sh
*** glibc detected *** double free or corruption (!prev): 0x08052548 **

I then tried to compil it, since not working with debian, and got this at make:

Code:

lpha/cvoicecontrol/microphone_config.c:1388: undefined reference to `waddnstr'
/tmp/cvoicecontrol-0.9alpha/cvoicecontrol/microphone_config.c:1339: undefined reference to `init_pair'
/tmp/cvoicecontrol-0.9alpha/cvoicecontrol/microphone_config.c:1340: undefined reference to `init_pair'
/tmp/cvoicecontrol-0.9alpha/cvoicecontrol/microphone_config.c:1341: undefined reference to `init_pair'
/tmp/cvoicecontrol-0.9alpha/cvoicecontrol/microphone_config.c:1342: undefined reference to `init_pair'
microphone_config.o: In function `setHighlight':
/tmp/cvoicecontrol-0.9alpha/cvoicecontrol/microphone_config.c:57: undefined reference to `wattr_on'
collect2: ld returned 1 exit status
make[3]: *** [microphone_config] Error 1
make[3]: Leaving directory `/tmp/cvoicecontrol-0.9alpha/cvoicecontrol'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/cvoicecontrol-0.9alpha/cvoicecontrol'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/cvoicecontrol-0.9alpha'
make: *** [all-recursive-am] Error 2


Quote:
/lib/libc.so.6
/lib/libc.so.6
GNU C Library stable release version 2.3.6, by Roland McGrath et al.
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21).
Compiled on a Linux 2.6.18 system on 2008-01-19.
Available extensions:
GNU libio by Per Bothner
crypt add-on version 2.1 by Michael Glad and others
GNU Libidn by Simon Josefsson
linuxthreads-0.10 by Xavier Leroy
BIND-8.2.3-T5B
libthread_db work sponsored by Alpha Processor Inc
NIS(YP)/NIS+ NSS modules 0.19 by Thorsten Kukuk
Thread-local storage support included.
For bug reporting instructions, please see:
<[http://www.gnu.org/software/libc/bugs.html](http://www.gnu.org/software/libc/bugs.html)

Quote:
ldd microphone_config
ldd: ./microphone_config: No such file or directory
Any ideas ?
thx
___

---

