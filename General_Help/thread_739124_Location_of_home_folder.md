---
title: "Location of home folder"
date: 2008-03-29
forum: General Help
---

### Post by Barabbas on 2008-03-29
Hey, I just moved to ubuntu 7.10, from windows and was wondering where my program files where located. I saw some places where they say it's located in the home folder, but when I go to Places.home folder.> i can't find my user name or installed program directory list

where can I find my program files directory.

---

### Post by mcduck on 2008-03-29
There is no "program files"-directory.

Different files are put to different places depending on what they are used for. For example, the executable binaries usually go to /usr/bin, documentation files go to /usr/share/doc, icons nad possibly other images to /usr/share/icons and /usr/share/pixmaps, library files to /usr/lib and so on. Programs may also have their own directory in /usr/share to keep files that don't have any other place in the system.. This is all done automatically by the package manager, so you don't need to worry about it.

Your personal settings for programs, however, are inside your home directory as hidden files. Press Ctrl-H in the file manager to see them.

To list installed programs use the Synaptic package manager (in System/Administration).

---

### Post by pbpersson on 2008-03-29
> **mcduck said:**
> There is no "program files"-directory.

Different files are put to different places depending on what they are used for. For example, the executable binaries usually go to /usr/bin, documentation files go to /usr/share/doc, icons nad possibly other images to /usr/share/icons and /usr/share/pixmaps, library files to /usr/lib and so on. Programs may also have their own directory in /usr/share to keep files that don't have any other place in the system.. This is all done automatically by the package manager, so you don't need to worry about it.


That is the first time I have heard that explained.  Is there a web site that goes into more detail?  Migrating from Windows, getting used to that aspect of Linux has been somewhat challenging.

---

### Post by Barabbas on 2008-03-29
Thanks very much, seriouslly this is like the best help forum ever.

---

### Post by mcduck on 2008-03-29
> **pbpersson said:**
> That is the first time I have heard that explained.  Is there a web site that goes into more detail?  Migrating from Windows, getting used to that aspect of Linux has been somewhat challenging.
These might be what you are looking for:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

I know, it might seem very confusing in the beginning, but actually you only need to know about couple important directories as everything is handled automatically and all your own stuff goes to your home directory anyway. Sooner or later you'll start seeing the logic behind all this, and the it'll make your life much easier than ever in Windows :D (for example, whenever you need to find some programs documentation, no matter what the program is you'll know the docs are /usr/share/doc as opposed to Windows where you'd need to find that programs directory inside Program Files, and then browse around that directory until you find where the programs installer placed the documentation..)

edit: There are also couple of commands you might want to know about, "whereis" and "which". Whereis shows programs files are installed, for example running "whereis firefox" will list all places where Firefox has some files. "Which" gives the location of the programs main executable file, for example running "which firefox" would reply "/usr/bin/firefox".

---

