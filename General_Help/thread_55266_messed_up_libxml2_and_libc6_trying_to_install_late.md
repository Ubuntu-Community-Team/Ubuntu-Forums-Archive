---
title: "messed up libxml2 and libc6 trying to install latest gtkpod"
date: 2005-08-08
forum: General Help
---

### Post by 23meg on 2005-08-08
yes, that's exactly what i did.  ](*,) 

i tried installing gtkpod 0.94.0-1, and to meet its dependencies i downloaded and attempted to install libxml2 2.6.20-1 and libc6 2.3.5.3-3 off the debian package repository. now my libxml2 and gtkpod packages are listed as broken in synaptic. when i try to reinstall / uninstall gtkpod synaptic crashes, and when i attempt to reinstall libxml2 synaptic offers to remove hundreds of packages.. same happens with "apt-get -f install" and when trying to remove gtkpod via the command line.

i'm on a stupid day. please help!

---

### Post by PeP on 2005-08-08
[QUOTE=23meg]yes, that's exactly what i did.  ](*,) 

i tried installing gtkpod 0.94.0-1, and to meet its dependencies i downloaded and attempted to install libxml2 2.6.20-1 and libc6 2.3.5.3-3 off the debian package repository. now my libxml2 and gtkpod packages are listed as broken in synaptic. when i try to reinstall / uninstall gtkpod synaptic crashes, and when i attempt to reinstall libxml2 synaptic offers to remove hundreds of packages.. same happens with "apt-get -f install" and when trying to remove gtkpod via the command line.

i'm on a stupid day. please help![/QUOTE]

It's time for you to learn your ways throught aptitude or dselect.

Enjoy ;-)

---

### Post by 23meg on 2005-08-09
alright, forgive my temporary stupidity... i sorted this out by upgrading to the exact (and not higher) libc6 version required by libxml2, and reconfiguring with dpkg-reconfigure.

---

