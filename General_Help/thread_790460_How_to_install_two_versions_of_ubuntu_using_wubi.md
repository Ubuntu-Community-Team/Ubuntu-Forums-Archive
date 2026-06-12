---
title: "How to install two versions of ubuntu using wubi?"
date: 2008-05-11
forum: General Help
---

### Post by pandu.rs on 2008-05-11
I would like to install two different versions of ubuntu using wubi. When i try to install second version of ubuntu, wubi installer only gives the option to uninstall previous first (which i don't want to, but install second version without uninstalling previously installed version). How can i do this?


Any ideas on how i can do this will be great. Thanks.

P.S: I am aware that i can install a new ubuntu version to a dedicated partition, but i do not want to do this for now.

---

### Post by pandu.rs on 2008-05-11
Maybe can i use UNetbootin to accomplish this?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by pandu.rs on 2008-05-11
Can i use UNetbootin to accomplish this?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Gripp on 2008-05-11
hmmm
not sure myself, but i would imagine it would be a little more manual than that.  it will want to install everything to to a folder called 'ubuntu'

so i suppose, if you renamed your first install folder, and changed your fstab and grub and windows boot.ini (i cant think of what else, but i'm sure there is) to match your new folder name, and then run wubi again it may make a new install...


i would wait until someone who knows everything that needs done posts though..

---

### Post by abn91c on 2008-05-13
you don't need to do all, if you want to have for instance ubuntu and kubuntu just open the synaptic or update manager then search for and  choose gnome-desktop or kubuntu-desktop whichever the case may be. during the download and installation it will ask which version you want as default: GDM or  KDE, select one. when downlad and install is finished log out and select which session you want to use, then enjoy. 
you can also open a terminal and do a sudo apt-get install kubuntu-desktop

---

### Post by Gripp on 2008-05-15
i just had a thought... why not just use Lubi in linux??

---

