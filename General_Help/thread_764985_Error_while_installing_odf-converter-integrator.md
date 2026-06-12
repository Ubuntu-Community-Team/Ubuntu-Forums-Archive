---
title: "Error while installing odf-converter-integrator"
date: 2008-04-24
forum: General Help
---

### Post by randomAccess on 2008-04-24
With openoffice that came with Ubuntu 7.10 I was able to open .docx and .xlsx files, but NOT TO SAVE them after making some changes. So I tried to fix this by reinstalling the package. However I received this error

```
~$ sudo dpkg -i ./Desktop/odf-converter-integrator-chocolate*deb
(Reading database ... 156920 files and directories currently installed.)
Unpacking odf-converter-integrator (from .../odf-converter-integrator-chocolate_0.1.4-1_i386.deb) ...
dpkg: error processing ./Desktop/odf-converter-integrator-chocolate_0.1.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu', which is also in package odf-converter
Errors were encountered while processing:
 ./Desktop/odf-converter-integrator-chocolate_0.1.4-1_i386.deb 

```

First I tried to remove existing integrator package, with no luck. Now I don't now what to do. Can anybody help me?

---

### Post by dr.koljan on 2008-05-06
> **randomAccess said:**
> With openoffice that came with Ubuntu 7.10 I was able to open .docx and .xlsx files, but NOT TO SAVE them after making some changes. So I tried to fix this by reinstalling the package. However I received this error

```
~$ sudo dpkg -i ./Desktop/odf-converter-integrator-chocolate*deb
(Reading database ... 156920 files and directories currently installed.)
Unpacking odf-converter-integrator (from .../odf-converter-integrator-chocolate_0.1.4-1_i386.deb) ...
dpkg: error processing ./Desktop/odf-converter-integrator-chocolate_0.1.4-1_i386.deb (--install):
 trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/MOOXFilter_cpp.xcu', which is also in package odf-converter
Errors were encountered while processing:
 ./Desktop/odf-converter-integrator-chocolate_0.1.4-1_i386.deb 

```

First I tried to remove existing integrator package, with no luck. Now I don't now what to do. Can anybody help me?

You'll have to remove odf-converter first.

---

