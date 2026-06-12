---
title: "apt-get... Getting all Debian Packages?"
date: 2005-05-02
forum: General Help
---

### Post by caspian on 2005-05-02
I was browsing SourceForge, and one of the projects instructed Debian users to run "apt-get install ..." But when I tried it, all it returned is this:

> Reading package lists... Done
Segmentation faulty tree... 0%

Is there something I need to do in order to apt-get Debian packages (not just Ubuntu packages)?

Also, is there a way I can search through apt-get's database?

Thanks!

---

### Post by neighborlee on 2005-05-02
[QUOTE=caspian]I was browsing SourceForge, and one of the projects instructed Debian users to run "apt-get install ..." But when I tried it, all it returned is this:



Is there something I need to do in order to apt-get Debian packages (not just Ubuntu packages)?

Also, is there a way I can search through apt-get's database?

Thanks![/QUOTE]
------------
the segfault part I find a little weird but...anyway debian packages downloaded from the internet are installed this way:

dpkg -i thispackage.deb

you can search the apt-get database with:

apt-cache search blah

good luck and welcome to ubuntu and debian..;-0

cheers
neighborlee

---

### Post by caspian on 2005-05-02
[QUOTE=neighborlee]------------
the segfault part I find a little weird but...anyway debian packages downloaded from the internet are installed this way:

dpkg -i thispackage.deb

you can search the apt-get database with:

apt-cache search blah

good luck and welcome to ubuntu and debian..;-0

cheers
neighborlee[/QUOTE]
 Thanks a bunch!

I really appreciate your help. :)

---

### Post by Gustav on 2005-05-03
Although almost every Debian package is included in Ubuntu if you add the universe repository. 

And mixing Debian and Ubuntu packages is not entirely safe.

---

### Post by az on 2005-05-03
"Reading package lists... Done
Segmentation faulty tree... 0% "

Maybe you need to do 

sudo dpkg --clear-avail

to clean up your screwed up package database...

---

