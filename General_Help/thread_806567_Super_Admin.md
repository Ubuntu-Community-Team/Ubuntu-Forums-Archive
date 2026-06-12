---
title: "Super Admin"
date: 2008-05-25
forum: General Help
---

### Post by zenithlt on 2008-05-25
I was trying to install Radeon HD3850 drivers from *.run file.

```
sh ./ati-driver-installer-8-5-x86.x86_64.run
```

After few second I got this:

[[IMG]http://img86.imageshack.us/img86/2420/screenshottl7.th.png[/IMG]](http://img86.imageshack.us/my.php?image=screenshottl7.png)

And when I click OK, nothing happens, why?

---

### Post by alarme on 2008-05-25
You must write:

sudo sh ./ati-driver-installer-8-5-x86.x86_64.run

This way, you run the program as super user

---

### Post by danwood76 on 2008-05-25
In ubutnu you cant install the drivers through their GUI you have to do it from the command line.

Here is a good guide for it:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29)

---

