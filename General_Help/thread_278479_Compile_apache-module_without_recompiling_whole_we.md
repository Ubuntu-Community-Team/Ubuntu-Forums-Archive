---
title: "Compile apache-module without recompiling whole webserver"
date: 2006-10-16
forum: General Help
---

### Post by zakhooi on 2006-10-16
Hi,

I'm running a default ubuntu server running apache/apache2:
```
# dpkg -l |grep apache
ii  apache                                 1.3.34-2ubuntu0.1                      versatile, high-performance HTTP server
ii  apache-common                          1.3.34-2ubuntu0.1                      support files for all Apache webservers
ii  apache-perl                            1.3.34-2ubuntu0.1                      versatile, high-performance HTTP server with
ii  apache-ssl                             1.3.34-2ubuntu0.1                      versatile, high-performance HTTP server with
ii  apache2                                2.0.55-4ubuntu2.1                      next generation, scalable, extendable web se
ii  apache2-common                         2.0.55-4ubuntu2.1                      next generation, scalable, extendable web se
ii  apache2-mpm-prefork                    2.0.55-4ubuntu2.1                      traditional model for Apache2
ii  apache2-utils                          2.0.55-4ubuntu2.1                      utility programs for webservers
ii  libapache-mod-acct-mysql               0.5-19ubuntu1                          Accounting module for Apache, mysql version
ii  libapache-mod-auth-mysql               4.3.1                                  Apache module for MySQL authentication
ii  libapache-mod-dav                      1.0.3-10                               A DAV module for Apache
ii  libapache-mod-dtcl                     1.0.1-2                                Server side Tcl scripting for Apache
ii  libapache-mod-perl                     1.29.0.4-2ubuntu0.1                    integration of perl with the Apache web serv
ii  libapache-mod-php4                     4.4.2-1build1                          server-side, HTML-embedded scripting languag
ii  libapache2-mod-php5                    5.1.2-1ubuntu3.2                       server-side, HTML-embedded scripting languag
```

Now I'd like to buildin a bandwith limiter: [http://www.ivn.cl/apache/#bandwidth](http://www.ivn.cl/apache/#bandwidth)

I think it should be possible to just compile this module without having to recompile to whole apache webserver.
I guess I need to install the apache-dev packages and then compile the bw_mod.c file manually.
And then add a LoadModule line in the apache conf-file.

From here I need assistance, so

- What additional packages do I need to install (both for apache as apache2)
- What steps need to be performed to compile,integrate/load the apache module in the current setup.

Thanks in advance.

---

### Post by zakhooi on 2006-10-20
*Kick*

---

