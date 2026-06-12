---
title: "SCIM &amp; openoffice"
date: 2007-09-29
forum: General Help
---

### Post by taggat on 2007-09-29
Can't get openoffice to write in Japanese.
I've read some of the fixes I found using the search function on this site
but I still can't get it to work

I've even tried to install other Application , Lotus, Staroffice ect... to try to get some office suite that will write in Japanese but to no avail, as Lotus and Staroffice refuse to work on my computer... Help!

Thanks taggat

---

### Post by taggat on 2007-10-06
SOLVED! 

Iif you are having the same problem of getting SCIM to work in Openoffice.org
the answer is to completely remove openoffice using the synaptic package manager
and download the deb from [http://download.openoffice.org/2.3.0/index.html](http://download.openoffice.org/2.3.0/index.html)

first extract the tar files move to the DEBS folder in it 

remove the KDE integration or Gnome which ever you don't use

then type sudo dpkg -i *.deb in the term

then move to desktop-integration

and then type sudo dpkg -i *.deb in the term and Japanese SCIM input works again

The problem seems to be the fact that Ubuntu installs a custom Openoffice with some bug fixes that break SCIM support

Thanks taggat
so if someone at ubuntu could look into fixing the fix that breaks SCIM I know I would appreciate it.

---

### Post by simplicissimus on 2007-10-07
I'm testing the **7.10 beta**. There, SCIM works only in the standard Gnome text-editor. For Openoffice, Firefox or all the other applications, I'm not able to enable SCIM.

Is it a known but since in 7.04 there were no such problems?

---

### Post by taggat on 2007-10-07
A fresh install of 7.04 will give you a openoffice that can use SCIM
but the first thing it wants to do is update openoffice, and after that update SCIM will no longer work
This will cure you of the version of openoffice that Ubuntu makes and give back one that can use SCIM

---

