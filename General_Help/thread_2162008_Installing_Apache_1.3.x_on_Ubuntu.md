---
title: "Installing Apache 1.3.x on Ubuntu"
date: 2013-07-12
forum: General Help
---

### Post by optize on 2013-07-12
Don't ask, but I need to find a way to install the source version of Apache 1.3.x on Ubuntu 12.04.2 LTS.

This is what it decides to spit out while installing:

--
> 
# ./configure --prefix=/var/www
Configuring for Apache, Version 1.3.42
 + Warning: Your 'echo' command is slightly broken.
 + It interprets escape sequences per default. We already
 + tried 'echo -E' but had no real success. If errors occur
 + please set the SEO variable in 'configure' manually to
 + the required 'echo' options, i.e. those which force your
 + 'echo' to not interpret escape sequences per default.

 + NOTE: You may also need to edit the shell invoked by
 +       'configure'. Some shells (e.g. dash) have a
 +       faulty echo builtin.
 + using installation path layout: Apache (config.layout)
Creating Makefile
Creating Configuration.apaci in src
Syntax error --- The configuration file is used only to
define the list of included modules or to set Makefile in src
options or Configure rules, and I don't see that at all:
 `$(SRCDIR)/apaci`
default
default
no
no
no
yes
no
default
no
default
default

--

Does anyone know where to even start troubleshooting this mess? I am using the bash shell, but have tried others with similar results.

---

### Post by optize on 2013-07-16
Fixed, for those who have the problem:

>  bash ./configure

After configure:

> sed -i 's/getline/apache_getline/' src/support/htdigest.c 
sed -i 's/getline/apache_getline/' src/support/htpasswd.c 
sed -i 's/getline/apache_getline/' src/support/logresolve.c

---

