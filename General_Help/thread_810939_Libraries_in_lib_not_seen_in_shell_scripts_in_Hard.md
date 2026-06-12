---
title: "Libraries in /lib not seen in shell scripts in Hardy"
date: 2008-05-28
forum: General Help
---

### Post by igoddard on 2008-05-28
I've updated from Dapper to Hardy.

I found I couldn't run the script to start Kylix.  A number of error messages are being returned from expr and sed which are used in the script and from kylix itself.  All are complaining that a shared library is missing, lib.so.6 in the case of expr & sed and libpthread.so.0 in the case of kylix.

eg:
has_slash=`expr "$kylixpath" : '\(.*//\)'`

Run from within the script this gives the message:

expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Run from the command line there's no problem.

Both these libs are in /lib so it looks as if commands in a script can't see /lib.

The script was fine in Dapper.

---

### Post by igoddard on 2008-05-29
I've now narroowed down the problem.  In order to run the kylix executable LD_ASSUME_KERNEL=2.4.1 is needed. According to [http://people.redhat.com/drepper/assumekernel.html](http://people.redhat.com/drepper/assumekernel.html) this requires libraries in /lib/i686 which isn't there.  Moving the LD_ASSUME_KERNEL line down from the start of the script to just before the invocation of the kylix executable itself removes the problems with expr and sed but the kylix executable fails.  It also fails if I change the value to 2.4.20.

It seems that I need the libs from /lib/i686 but they were removed in the course of the upgrade.  Does anyone know the appropriate package for them?

Ian

---

