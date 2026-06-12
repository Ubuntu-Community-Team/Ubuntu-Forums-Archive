---
title: "I get an error when trying to compile package..."
date: 2008-05-14
forum: General Help
---

### Post by Lord Xeb on 2008-05-14
I am trying to compile a package called "gnome-hdaps-applet-20060120.tar.gz". I extract it, then do "cd to that file on my desktop. Next I am suppose to enter in this command:

```
gcc $(pkg-config --cflags --libs libpanelapplet-2.0) -o gnome-hdaps-applet gnome-hdaps-applet.c
```


But I get the following:

```
Package libpanelapplet-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpanelapplet-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpanelapplet-2.0' found
gcc: gnome-hdaps-applet.c: No such file or directory
gcc: no input files
```


:/ What do I do?

HDAPS (**H**ard **D**rive **A**ctive **P**rotection **S**ystem)

I have an IBM T43 model 2669.

---

### Post by chrisccoulson on 2008-05-14
```
sudo apt-get install libpanel-applet2-dev
```
Your error also suggests you aren't in the right directory ('gcc: gnome-hdaps-applet.c: No such file or directory' suggests your source file can't be found)

---

### Post by Lord Xeb on 2008-05-20
But the damn things exists and I am in the right directory... I just gave up all together

---

### Post by hamidaddin on 2009-02-15
> **chrisccoulson said:**
> ```
sudo apt-get install libpanel-applet2-dev
```




[SIZE="3"]Thanks **chrisccoulson**:KS:KS. I had the same promlem trying to compile a panel applet and your suggestion solved it for me.[/SIZE]

---

