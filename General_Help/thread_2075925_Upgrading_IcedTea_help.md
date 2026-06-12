---
title: "Upgrading IcedTea help"
date: 2012-10-24
forum: General Help
---

### Post by Champlin93 on 2012-10-24
When I try to use Java in Google Chrome it says that: 
> "Iced Tea was blocked because it is out of date"
and gives me an option of either: 
> "Run this time" 
or 
> "Update plug-in" 
Running does nothing so I tried to update and that took me to [http://icedtea.classpath.org/wiki/Main_Page](http://icedtea.classpath.org/wiki/Main_Page). 
So I can't figure out for the life of me what this website wants me to do. I followed the "IcedTea7" link to where I guess I'm supposed to get it [http://blog.fuseyism.com/index.php/2012/10/19/security-icedtea-1-10-10-1-11-15-2-1-3-2-2-3-2-3-3-released/](http://blog.fuseyism.com/index.php/2012/10/19/security-icedtea-1-10-10-1-11-15-2-1-3-2-2-3-2-3-3-released/) and downloaded [http://icedtea.classpath.org/download/source/icedtea6-1.11.5.tar.gz](http://icedtea.classpath.org/download/source/icedtea6-1.11.5.tar.gz) (idk why there wasn't a version 7 since that's the link I clicked) 
The instructions on the Iced Tea website say: 
> Firstly, download the latest release of IcedTea6; see above. We recommend the one with the highest version number. You should then unpack and build the release as follows:
$ ./configure
$ make
These aren't complete commands and I'm not sure what to put. I'm pretty comfortable with a terminal but I really have no Idea what to do hear.
I checked chrome://plugins/ and it says I have version Iced Tea 1.2.
Is there an simpler way to do this?

---

### Post by polki@mac.com on 2012-10-25
Starting chrome with "/opt/google/chrome/google-chrome --allow-outdated-plugins %U" worked for me.

---

### Post by Champlin93 on 2012-10-25
The problem is my version of Iced Tea is too ancient to run most of the time and often crashes. I need to actually update it.

---

