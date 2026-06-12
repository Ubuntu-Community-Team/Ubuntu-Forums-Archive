---
title: "Uninstalling &quot;make install&quot;-ed programs"
date: 2007-06-20
forum: General Help
---

### Post by rudlavibizon on 2007-06-20
A noob question: How do I uninstall programs that have been installed with ./configure, make, make install?

I successfully compiled a program called veejay, and it runs fine, but I would like to change a configure flag and reinstall it. Do I have to uninstall it to do so in the first place?

Also, to compile veejay, I needed to install the newest (svn or cvs) ffmpeg. To be on the safe side i uninstalled the version which is in the repo and apt removed a program called synfig studio with it (a dependency of ffmpeg as I understand). Later I installed synfig studio and ffmpeg (the repo version). So now I have two of those ffmpegs installed. Will this do something bad to my system?

---

### Post by DracoPsycho on 2007-06-20
You just do make uninstall, still being in the directory with sources (where makefile lies). It won't work if unistall procedure isn't in the makefile, though. But if it's well maintained package it should have it. 

Regarding ffmpeg. I think that it's safe, depends where your program searches for ffmpeg it will use one or another.

---

### Post by rudlavibizon on 2007-06-20
Thanks

---

### Post by Brucevdk on 2007-06-20
I was writing this reply before DracoPsycho replied. I see he/she answered your question, but I don't want to let my reply go to waste :)

> **rudlavibizon said:**
> A noob question: How do I uninstall programs that have been installed with ./configure, make, make install?
You can use *make uninstall*, which usually works since most programs include this target. 

Also there's a program called *checkinstall* (sudo apt-get install checkinstall) which allows you to create Debian packages, It doesn't always work but when it does it's quite useful. Instead of ./configure && make && make install you use:

```

./configure
make
checkinstall # if you use sudo it also installs the .deb

```

This obviously gives you the advantage of uninstalling it through the normal tools.

> **rudlavibizon said:**
> 
I successfully compiled a program called veejay, and it runs fine, but I would like to change a configure flag and reinstall it. Do I have to uninstall it to do so in the first place?

I don't think so.

> **rudlavibizon said:**
> 
Also, to compile veejay, I needed to install the newest (svn or cvs) ffmpeg. To be on the safe side i uninstalled the version which is in the repo and apt removed a program called synfig studio with it (a dependency of ffmpeg as I understand). Later I installed synfig studio and ffmpeg (the repo version). So now I have two of those ffmpegs installed. Will this do something bad to my system?

I don't think it'll do anything *bad* perse, just clutters your system. I might be wrong, but I think the worst that can happen is that some application picks the older version of the library.

---

### Post by DracoPsycho on 2007-06-20
rudlavibizon: I'm sorry that your post have been later. It's much nicer than mine ;)

---

