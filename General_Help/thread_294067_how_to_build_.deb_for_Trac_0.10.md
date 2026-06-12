---
title: "how to build .deb for Trac 0.10?"
date: 2006-11-06
forum: General Help
---

### Post by Max Ischenko on 2006-11-06
I'm trying to install Trac 0.10 (which is not available in repos for dapper/edgy) but I want to build a .deb for it to install 'properly'.

I have tried checkinstall command but it doesn't work for some reason:

$ checkinstall -D --install --include /usr/lib/python2.4/site-packages/trac python ./setup.py install

Installing with python ./setup.py install...

========================= Installation results ===========================
running install
running build
running build_py
copying trac/siteconfig.py -> build/lib/trac
running build_scripts
running install_lib
creating /usr/lib/python2.4/site-packages/trac
copying build/lib/trac/About.py -> /usr/lib/python2.4/site-packages/trac
error: /usr/lib/python2.4/site-packages/trac/About.py: No such file or directory
****  Installation failed. Aborting package creation.

Bye.


What is the correct way to build a .deb for Trac (using checkinstall or not)?

---

