---
title: "Desktop effects could not be enabled"
date: 2008-04-30
forum: General Help
---

### Post by GabrielWolff on 2008-04-30
When trying to enable the Visual Effects under System->Preferences->Appearance, I keep getting this message:
```
Desktop effects could not be enabled
```

Guess someone maust have gotten this message other than me, but I couldn"t find anything helpful in the forums.

I am working on a lenovo T60.

---

### Post by hermes0710 on 2008-04-30
What is your graphics card? If it is nvidia/ati you must install the restricted driver:

System > Administration > Hardware Manager

Find the entry with your graphic card and tick the check box to enable it (You must have internet connection in order to allow the manager to have the driver downloaded). Then you will be asked to reboot.

---

### Post by toobitz on 2008-04-30
If the above doesn't help, open a terminal window and enter the following:
```
compiz --replace
```
then paste the output here. Also, you may want to run
```
LIBGL_DEBUG=verbose glxinfo
```
in a terminal and paste the output here. And tell us what kind of graphics card you are using, as the previous poster already wrote.

---

### Post by GabrielWolff on 2008-04-30
The above helped,

Thank you :)


G

---

