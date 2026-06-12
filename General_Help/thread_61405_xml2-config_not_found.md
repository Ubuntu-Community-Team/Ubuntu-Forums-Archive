---
title: "xml2-config not found"
date: 2005-08-31
forum: General Help
---

### Post by rold50 on 2005-08-31
I'm trying to install a program called gazebo.

when I do ./configure

it does all the checks until it checks for xml2-config and it says something like that xml2-config not found and that I need libxml2.

I checked my synaptic manager and libxml2 is already installed.

however I can't seem to find the xml2-config. I do locate -r xml2-config and it returns nothing. There are, however a couple of libxml2 libraries in /usr/lib/ however there's no /usr/lib/xml2-config

What should I do? Is there a way to add that? I was under the assumption that xml2-config should already be part of the libxml2 package. I tried reinstalling my libxml2 package and still no xml2-conif. I don't know why I can't seem to find it.

---

### Post by DJ_Max on 2005-08-31
Make sure you have the dev package.

---

### Post by MSBF on 2008-07-21
Thanks

---

