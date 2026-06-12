---
title: "Managing one ubuntu configuration on multiple machines"
date: 2006-11-16
forum: General Help
---

### Post by neilernst on 2006-11-16
I have a work PC and a home PC, both with Ubuntu Edgy. I often find myself reinstalling software on one computer that I had put on the other one. 

Is there a tool for synchronizing the state of the user applications that I've apt-get'ed? Ideally I could go home, hit 'synch' and any packages I installed at work would be automatically selected and installed. I can think of writing a script that would push any package additions to a remote server, but I wanted to see if this was already done.

Clearly this can't apply to hardware-specific packages like drivers, for example.

---

### Post by koenn on 2006-11-16
you can list installed packages with ```
dpkg --list
``` or ```
dpkg --list > packagelist
``` The latter writes the list to a text file "packages", which could probably be used as a starting point to install the same packages on a 2nd system. Packages in the list that are already installed would just return " ... already newest version" so that's ok. 
hardware-specific packages may be more problematic.

you could also use rsync to synchronise the apt status files and /or directories where packages are installed (+ their config files, ....) 

I have no knowledge of any existing tools. Maintaining identical systems is usually done either with something server-based (eg edubuntu, LTSP, ...) or some form of centralised software management, i guess.

---

