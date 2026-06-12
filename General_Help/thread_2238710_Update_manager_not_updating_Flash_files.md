---
title: "Update manager not updating Flash files"
date: 2014-08-09
forum: General Help
---

### Post by John_Carver on 2014-08-09
Ubuntu 12.04 LTS on AZUS 
Update Manager has two updates that won't install

GTE+ control panel for Adobe Flash Player plugin version 11
Adobe Glash Player plugin version 11

Imagine files may be corrupted but not sure how to correct it.

---

### Post by Impavidus on 2014-08-09
Do you get any error messages? Try it in the terminal:```
 sudo apt-get upgrade
```and post error messages here.

---

### Post by John_Carver on 2014-08-09
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by John_Carver on 2014-08-10
Just checked Firefox plugins and the current version is already installed.
11.2.202.394
That is one of the two files in the update.
So, not sure what is going on

---

### Post by Rob Sayer on 2014-08-10
If a package is being held back in apt-get upgrade it means that the package will be replaced, not just updated.  This most often happens with new kernel versions.  But I've seen it with other things and I updated them successfully.

What I'd do there is:

```
sudo apt-get update

sudo apt-get dist-upgrade
```

which will replace older packages with the new version.  I only do this if something is being held back, I do apt-get update and apt-get upgrade by habit in the terminal.

---

### Post by John_Carver on 2014-08-10
Just cleared out the update manager of the two files.

Checked Firefox plugins and Flash was installed with the current version.  Unknown to me why the manager was  trying to redo the install.

Anyway, got to thinking that Update Manager-Software Sources-other sources might hold a clue. I unchecked everything, did a reload, and the files were gone.

Next, I starting rechecking them one at a time to reload and found the culprit.  :archive cannical/ubuntu/trusty partner.  This is the line reloading the two unwanted files.  Not sure why "trusty" is there because it is not on my other computer.  Maybe the 64 bit version has something to do with it.

Nice to see them gone---for the time being.

Thanks for your tip.. will try that also

---

