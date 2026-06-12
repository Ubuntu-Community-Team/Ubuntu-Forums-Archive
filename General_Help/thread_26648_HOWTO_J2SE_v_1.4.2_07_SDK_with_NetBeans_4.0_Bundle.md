---
title: "HOWTO: J2SE v 1.4.2_07 SDK with NetBeans 4.0 Bundle and Firefox"
date: 2005-04-13
forum: General Help
---

### Post by nutubu on 2005-04-13
I'll add yet another thread on configuration of Java with Firefox. I tried quite a few procedures from other threads but none worked.

I installed [J2SE v 1.4.2_07 SDK with NetBeans 4.0 Bundle](http://java.sun.com/j2se/1.4.2/download-netbeans.html) in my home directory.

The only thing I have to add to make Firefox work is a symbolic link to the right plugin:

cd ~/.mozilla/plugins
ln -s ~/j2sdk1.4.2_07/jre/plugin/i386/ns610-gcc32/libjavaplugin_oji.so

This was sufficient to make Firefox support java applets.

To be able to launch java from the comand line, I added the bin directory of where j2sdk is installed to my ~/.bashrc file:

PATH=~/j2sdk1.4.2_07/bin:$PATH

---

### Post by jdong on 2005-04-13
Please do not post questions in the Tips & Tricks forum... It's reserved for posting actual articles.

---

