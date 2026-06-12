---
title: "Uninstall IceTea Java"
date: 2013-06-29
forum: General Help
---

### Post by lumaja on 2013-06-29
I was advised to uninstall IceTea Java and install Oracle Sun Java by other application forum.
 Is this safe on my OS Ubuntu 12.04 precise running Virtualbox with Windows Xp.
 I don’t know any of them I’m lost.
 Need guidelines to uninstall and install Please.
 Thank you

---

### Post by QIII on 2013-06-29
Hello!

I'm unable to tell if you mean you have Ubuntu as the host or guest, but that doesn't matter much.

You don't need to uninstall IcedTea or OpenJDK 7.  OpenJDK 7 can coexist with Oracle Java 7 just fine.  You can choose at any time which one you want to be used.

The easiest way to install Oracle Java 7 in Ubuntu can be found [here.]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

This will add a trusted PPA (Personal Package Archive -- think of it sort of like an extra little repo), install Oracle Java 7 from Oracle's website, set it as the default, install the web browser add-in and it will update Oracle Java 7 when Oracle publishes an update.  So you don't have to do anything special besides running your normal update/upgrade to keep up to date.

Best wishes!

---

