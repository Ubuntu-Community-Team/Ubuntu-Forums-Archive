---
title: "Gdeb Doesnt install deb files"
date: 2007-11-27
forum: General Help
---

### Post by markk1994 on 2007-11-27
Hey my Gdeb doesnt seem to install any deb files any alternatives to gdeb?

---

### Post by erginemr on 2007-11-27
Hi,

Normally when you double-click on a deb file, Gdebi should interfere, ask for your root password and take over the installation. 

You can also install Debian packages form the command line with:
sudo dpkg -i package_name.deb
or
sudo dpkg --install package_name.deb

EDIT: However, I am not sure if GDebi is installed under Kubuntu.

---

### Post by Seisen on 2007-11-27
In Kubuntu instead of gdebi its called gdebi-kde and it wasn't implemented until gutsy so that might be why it is not working.

---

