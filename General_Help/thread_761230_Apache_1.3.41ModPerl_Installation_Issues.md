---
title: "Apache 1.3.41/ModPerl Installation Issues"
date: 2008-04-21
forum: General Help
---

### Post by Jayemdaet on 2008-04-21
Hi All

I am attempting to compile Apache 1.3.41 with ModPerl on Ubuntu 7.10 Server. I receive the following error when I try to start apache:

```
$ /usr/local/apache/bin/apachectl start
Syntax error on line 329 of /usr/local/apache/conf/httpd.conf:
Invalid command 'Order', perhaps mis-spelled or defined by a module not included in the server configuration
```

I get the same with configtest.

I also did a httpd -l and got only:

```
$ /usr/local/apache/bin/httpd -l
Compiled-in modules:
  http_core.c
suexec: disabled; invalid wrapper /usr/local/apache/bin/suexec
```


I installed and compiled using the following:

In mod_perl:
```
perl Makefile.PL APACHE_SRC=../apache_1.3.41/src DO_HTTPD=1 USE_APACI=1 PREP_HTTPD=1 EVERYTHING=1
```

In Apache:
```
./configure --prefix=/usr/local/apache --activate-module=src/modules/perl/libperl.a 
```

I do this exactly in Fedora 5 and I get:

```
$ /usr/local/apache/bin/httpd -l
Compiled-in modules:
  http_core.c
  mod_env.c
  mod_log_config.c
  mod_mime.c
  mod_negotiation.c
  mod_status.c
  mod_include.c
  mod_autoindex.c
  mod_dir.c
  mod_cgi.c
  mod_asis.c
  mod_imap.c
  mod_actions.c
  mod_userdir.c
  mod_alias.c
  mod_access.c
  mod_auth.c
  mod_setenvif.c
  mod_perl.c

suexec: disabled; invalid wrapper /usr/local/apache/bin/suexec
```

What am I missing here? Any help will be appreciated!

---

### Post by colo on 2008-04-21
Sorry not to directly help with my first post to this thread, but: why Apache 1.3? WHy not use the much more modern 2.2-branch with mod_perl? Would save you the hassle with compiling and installing yourself.

---

### Post by Jayemdaet on 2008-04-21
Due to there are certain modules I am using that have not been ported.

---

### Post by Jayemdaet on 2008-04-22
Does anyone have any ideas on this? Is it that Apache cannot be compiled correctly in Ubuntu? I am at a loss for why this is happening.

---

### Post by Jayemdaet on 2008-04-23
bump

---

