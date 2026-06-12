---
title: "Auto installing programs upon trying to remove others"
date: 2013-02-01
forum: General Help
---

### Post by djhvt on 2013-02-01
Hi All,

After installing Lubuntu I wanted to delete some unwanted programs, pretty standard fair. The thing is if a remove a program whether it be through the software center, synaptic, or the command prompt the system automatically replaces the applications I try to remove with other similar applications.

For example:

I remove Abiword, the system installs Libre writer
I remove Chromium, the system installs Firefox

If I try to remove the new apps it keeps going...for instance if I remove Firefox, the system installs Konqueror

Also all attempts to abort the install of these new applications is ignored. 

Whats up with this strange voodoo?

---

### Post by Locus Kiesselbachi on 2013-02-11
Strange!
How it installs without your permission? Impossible!

---

### Post by IanW on 2013-02-11
First, remove the metapackage "lubuntu-desktop" - this is what insists you need a word processor, web broswer, etc.

---

### Post by Rex Bouwense on 2013-02-11
I believe that is normal for Lubuntu.  Your system is not borked.  A way around it is to install the browser you want before un-installing chromium.  For instance if you want Opera, install it first and then do your uninstall.

---

