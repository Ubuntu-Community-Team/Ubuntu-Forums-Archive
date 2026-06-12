---
title: "error installing Apache"
date: 2007-04-12
forum: General Help
---

### Post by yg17 on 2007-04-12
I tried to install Apache on Feisty using apt-get, but it gave me this error:

Setting up libaprutil1 (1.2.7+dfsg-2build1) ...

Setting up apache2-utils (2.2.3-3.2build1) ...
Setting up apache-common (1.3.34-4.1) ...

Setting up apache (1.3.34-4.1) ...
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions on how to fix this? Thanks

---

### Post by kidders on 2007-04-13
Hi there,

Your system logs should help you identify the cause of "subprocess post-installation script returned error exit status 1". Without knowing what's gone wrong, there's no way to know how to fix it, I'm afraid.

---

### Post by az on 2007-04-13
Do you have any foreign repositories enabled?  Why are you installing apache instead of apache2?

To fix a broken package,

sudo apt-get -f install

---

