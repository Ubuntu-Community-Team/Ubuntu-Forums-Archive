---
title: "Error using &quot;make depend&quot;"
date: 2008-01-11
forum: General Help
---

### Post by MalcolmCowen on 2008-01-11
I'm compiling OpenLDAP from the downloadable sources from the LDAP site.

The configure script runs, then tells me to run "make depend"
So I run it and it fails.

What does "make depend" do?   I assumed it would compile a program called depend.

But there is no such program to be compiled.
so 
1, what would "make depend" do or try to do?
2, what is the cause of the failure I am getting (there is no man mkdep entry)

====================================================
Please run "make depend" to build dependencies
mc@Mitch:~/openldap$ make depend
Making depend in /home/mc/openldap
  Entering subdirectory include
make[1]: Entering directory `/home/mc/openldap/include'
Making ldap_config.h
make[1]: Leaving directory `/home/mc/openldap/include'
 
  Entering subdirectory libraries
make[1]: Entering directory `/home/mc/openldap/libraries'
Making depend in /home/mc/openldap/libraries
  Entering subdirectory liblutil
make[2]: Entering directory `/home/mc/openldap/libraries/liblutil'
../../build/mkdep  -d "." -c "cc" -m "-M" -I../../include        -I../../include      base64.c csn.c entropy.c sasl.c signal.c hash.c passfile.c md5.c passwd.c sha1.c getpass.c lockf.c utils.c uuid.c sockpair.c avl.c tavl.c ldif.c fetch.c testavl.c setproctitle.c getpeereid.c detach.c 
: invalid option
Usage:  /bin/sh [GNU long option] [option] ...
        /bin/sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)
        -abefhkmnptuvxBCHP or -o option
make[2]: *** [depend-common] Error 2
make[2]: Leaving directory `/home/mc/openldap/libraries/liblutil'
make[1]: *** [depend-common] Error 1
make[1]: Leaving directory `/home/mc/openldap/libraries'
make: *** [depend-common] Error 1
mc@Mitch:~/openldap$

---

### Post by snowjm on 2008-01-11
depend would be an option that you are passing to the make command, typically the Makefile is where that would be defined.

---

