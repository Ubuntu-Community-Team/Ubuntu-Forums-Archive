---
title: "dpkg: dependency problems prevent configuration of ubuntu-standard:"
date: 2006-11-16
forum: General Help
---

### Post by jimmyp on 2006-11-16
I upgraded from dapper to edgy yesterday by using update-manager.  I got an error when it upgraded at and when it upgraded ubuntu-standard but proceeded.  Now in edgy whenever I use apt-get I get this error:

Setting up at (3.1.10ubuntu3) ...
 * Starting deferred execution scheduler atd                                                                                                                    invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 at
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix it?

---

