---
title: "dpkg can't find installed package"
date: 2007-06-12
forum: General Help
---

### Post by mail480697 on 2007-06-12
I am attempting to install the latest version of gramps (gramps-project.org) and am getting funny errors:

$ sudo dpkg --simulate -i /tmp/gramps_2.2.8-1ubuntu1_all.deb
(Reading database ... 157968 files and directories currently installed.)
Preparing to replace gramps 2.2.8-1ubuntu1 (using .../gramps_2.2.8-1ubuntu1_all.deb) ...
jerryb@TheBrittons:~$ sudo dpkg -i /tmp/gramps_2.2.8-1ubuntu1_all.deb
(Reading database ... 157968 files and directories currently installed.)
Preparing to replace gramps 2.2.8-1ubuntu1 (using .../gramps_2.2.8-1ubuntu1_all.deb) ...
Unpacking replacement gramps ...
***
* Updating MIME database in /usr/share/mime...
Wrote 490 strings at 20 - 28f4
Wrote aliases at 28f4 - 2aa8
Wrote parents at 2aa8 - 3478
Wrote literal globs at 3478 - 34dc
Wrote suffix globs at 34dc - 69f4
Wrote full globs at 69f4 - 6a18
Wrote magic at 6a18 - c2d0
Wrote namespace list at c2d0 - c2e0
***
dpkg: dependency problems prevent configuration of gramps:
 gramps depends on python (>= 2.5); however:
  Version of python on system is 2.4.3-11ubuntu3.
dpkg: error processing gramps (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gramps

The issue seems to be with python.  However I have both 2.4 and 2.5 installed:

$ aptitude search python | grep ^i

[snip]

i   python2.4                       - An interactive high-level object-oriented 
i   python2.4-dictclient            - Python client library for DICT (RFC2229) p
i   python2.4-examples              - Examples for the Python language (v2.4)   
i   python2.4-gd                    - Python module wrapper for libgd           
i   python2.4-id3lib                - id3lib wrapper for Python - library       
i   python2.4-librdf                - Python 2.4 language bindings for the Redla
i   python2.4-minimal               - A minimal subset of the Python language (v
i   python2.5                       - An interactive high-level object-oriented 
i   python2.5-minimal               - A minimal subset of the Python language (v

So, why doesn't dpkg find 2.5?

---

