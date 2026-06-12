---
title: "Gnome help menu's etc"
date: 2004-11-16
forum: General Help
---

### Post by adept22 on 2004-11-16
Hi all Im a bit new to using Gnome, and i was wondering if anybody can help me in regards to adding things to the "start menu" not sure what else to call it. Also how is it possible to add a link to the desktop which points to a directory. ie /user/home etc? a

and as far as installing applications where is a good place to put them so that are available to all users? and if i install an app from synaptic will that autocreate an icon? if not how do i get it to run?

THanks for any help

---

### Post by jdodson on 2004-11-16
moved to correct forum.

---

### Post by piedamaro on 2004-11-16
[QUOTE=adept22]Hi all Im a bit new to using Gnome, and i was wondering if anybody can help me in regards to adding things to the "start menu" not sure what else to call it.
[/QUOTE]
Open your home folder, press control+L , write 
applications: 
in it (note the column), and click on open. There you can add, remove and edit menu entries.
If you want to change the menu for all the users, use
applications-all-users:

Another way is to raise your "start" menu, (we call it foot menu :P), and right click on a menu element. You can remove add and edit from there too.

[QUOTE=adept22]
 Also how is it possible to add a link to the desktop which points to a directory. ie /user/home etc? a[/QUOTE]
Open your file manager, then drag your directory on the desktop, while holding control + alt (you'll see the mouse pointer will change shape), and drop it.

[QUOTE=adept22]
and as far as installing applications where is a good place to put them so that are available to all users? and if i install an app from synaptic will that autocreate an icon? if not how do i get it to run?

THanks for any help[/QUOTE]
If you install applications with precompiled packages (as you do with synaptic), they are installed in order to be available to all users. There are also really good chances that you'll find a new entry on the menu, as soon as you install the package. However some packages do not put menu entries (like e.g. nvidia-settings).
In this case if you right click on a package while in synaptic, and choose "properties" you'll be able to see which files are contained in that package. You'll want to see which executables are installed, they are the ones under /usr/bin. (or /sbin or /usr/sbin if system executables).

---

### Post by WW on 2004-11-17
For editing the Applications menu, you can find more information here:

  [http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#applicationsmenu](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#applicationsmenu)

---

### Post by nehalem on 2004-11-17
Even though this information is very helpful I must say it's kind of perplexing why it needs to be done through such a backwards way.  I mean adding items to submenu's is a no brainer and refreshingly simple (I always hated how Fedora disabled adding new items) but why can't you edit the entire menu in a simiarly simple way.  I know this isn't an ubuntu issue but rather a gnome one. 

Is there something about the way that gnome produces menu's that prevent it from being simpler (at least without a lot of work)?

It would very nice to be able to add other locations under the computer menu.

---

