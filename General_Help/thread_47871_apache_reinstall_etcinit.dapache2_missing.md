---
title: "apache reinstall: /etc/init.d/apache2 missing"
date: 2005-07-10
forum: General Help
---

### Post by tigerstripedcat on 2005-07-10
This happens whenever I have to reinstall a package with apt-get.

I'm missing /etc/init.d/apache2, and even if it is created it sending the command restart to it does nothing.

A simple apache reinstall through kynaptic doesnt work
A simple remove and then install through kynaptic doesn't work either.

So my new process:
-using kynaptic remove ALL apache packages.
-updatedb and locate all apache2 files on my comptuer
-delete all relevant configfiles or files that I think might be holding back a reinstall
-sudo apt-get install apache2

But still no /etc/init.d/apache2!   

I imagine there's some great way to do this with apt-get that I'm just not familar with.  Maybe some forced removal, update, reinstall thing?

Can someone please help me?

Thanks

---

### Post by tigerstripedcat on 2005-07-10
anyone?

---

### Post by thagame on 2005-07-11
is there a /etc/init.d/httpd

i installed the alpha apache (2.1.6) and its /etc/init.d/httpd

---

