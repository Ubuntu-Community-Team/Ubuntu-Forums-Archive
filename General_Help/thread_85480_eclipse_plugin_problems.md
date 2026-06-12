---
title: "eclipse plugin problems"
date: 2005-11-02
forum: General Help
---

### Post by logophobia on 2005-11-02
I can't seem to install plugins on eclipse, it keeps saying:
Unable to complete action for feature "Eclipse C/C++ Development Tools" due to errors.
  Unable to create file "/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar". [/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar (No such file or directory)]
  Unable to create file "/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar". [/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar (No such file or directory)]

Same aprox. for the ruby dev tools plugin.

I tryed reinstalling it (with --purge option), creating the directories manually and some other stuff but it still doesn't work.

Any ideas?

---

### Post by bettlebrox on 2005-11-08
You don't have permissions to write to those directories.

---

### Post by jdgiotta on 2005-11-15
Do you suggest change the permissions on that folder(s)?

---

### Post by cstudent on 2005-11-15
You can either change the permissions of the directory eclipse resides in or when you want to install or update eclipse just run it from the terminal with:

sudo eclipse

I didn't like the repository install of eclipse for this reason. I uninstalled it and installed the official tar file from the eclipse website into the /opt directory.


Bill

---

### Post by jdgiotta on 2005-11-16
Should I go by the wiki instructions for manual install?

---

### Post by arpunk on 2005-11-28
Well actually no, its easy to get it working but a bit tricky:

```
sudo apt-get install eclipse-source
```

To get rid of those errors and then:

```
sudo eclipse
```

For installing plugings via "Help" menu, then you can use eclipse normally and plugins will load alright. Dont forget to ```
sudo eclipse
``` when you are going to install new plugins, that will make it easier since you dont know to change permissions. ;)

---

### Post by _bacon_ on 2005-11-29
I'd just get the .tar.gz from eclipse.org and extract it to my home directory. You can work from there no problem. You just have to watch for updates but since updating can break the plugins it's better to do it manually.

---

### Post by jdgiotta on 2005-11-29
The manual 'install' worked best. I had too much trouble installing Eclipse from the repositories.

---

### Post by TylerH on 2006-03-26
awesome, thanks for the help

what does everyone think of Eclipse as a c++ IDE? 
I use it for Java and think it's great, but haven't used it for C++ yet.

---

