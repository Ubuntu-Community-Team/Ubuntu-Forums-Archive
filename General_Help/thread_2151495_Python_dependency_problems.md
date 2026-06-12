---
title: "Python dependency problems"
date: 2013-06-04
forum: General Help
---

### Post by dinonet on 2013-06-04
I've been trying to get the bitlbee-skype plugin to work and have run into this issue with python. For the life of me I can't figure out why it won't install or why I can't repair these errors.

```
subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-gnutls:
 python-gnutls depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.
dpkg: error processing python-gnutls (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-openssl:
 python-openssl depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.
dpkg: error processing python-openssl (--configure):
 dependency problems - leaving unconfigured
Setting up python-pam (0.4.2-12.1ubuntu1.10.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    /var/lib/dpkg/info/python-pam.postinst: 10: pycentral: not found
dpkg: error processing python-pam (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-pkg-resources (0.6.10-4ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/python-pkg-resources.postinst: 10: pycentral: not found
dpkg: error processing python-pkg-resources (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-serial (2.3-1) ...
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/python-serial.postinst: 9: pycentral: not found
dpkg: error processing python-serial (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python-zope.interface:
 python-zope.interface depends on python-pkg-resources; however:
  Package python-pkg-resources is not configured yet.
dpkg: error processing python-zope.interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zope.interface (>= 3.5); however:
  Package python-zope.interface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of skyped:
 skyped depends on python-gnutls; however:
  Package python-gnutls is not configured yet.
dpkg: error processing skyped (--configure):
 dependency problNo apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         ems - leaving unconfigured
Errors were encountered while processing:
 python-support
 python-gnutls
 python-openssl
 python-pam
 python-pkg-resources
 python-serial
 python-zope.interface
 python-twisted-core
 skyped
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Am I totally corrupted or is there anything I can do?

---

### Post by dinonet on 2013-06-06
I get this when trying to run byobu ```
-bash: /usr/bin/python: No such file or directory
```

Does anyone know what happened here and how to possibly repair this?

---

