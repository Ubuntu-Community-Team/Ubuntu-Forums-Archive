---
title: "apt-get dist-upgrade errors"
date: 2006-07-21
forum: General Help
---

### Post by buijenre on 2006-07-21
I am trying to upgrade and I get this error:

root@RENSE:/var/lib# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not installed.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of request-tracker3.4:
 request-tracker3.4 depends on libxml-simple-perl; however:
  Package libxml-simple-perl is not configured yet.
dpkg: error processing request-tracker3.4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-simple-perl
 request-tracker3.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

If I try to remove request-tracker3.4 I get the same errors (or at least related to the perl stuff, which I do not which to remove.

Anyone know how to fix this?

---

