---
title: "install to a directory other than /usr/bin"
date: 2005-05-12
forum: General Help
---

### Post by GOwin on 2005-05-12
Im trying to cofigure an application for my ubuntu installation.

I am instructed to
> Configure it to make sure installation path is in /usr/local
    # ./configure --prefix=/usr/local
    Note: if you want to change to another directory, you better understand how to 
    read source of /path_to_source_of_playsms/bin/* files written in bash script

Since I use synaptic to do the installation, I don't control where it places the program.

How do I override this and install it to another directory instead?

---

### Post by ltmon on 2005-05-12
What application is this?

Ubuntu usually has everything configured to use /usr (./configure --prefix=/usr) and installing elsewhere will lead to problems.

I'd suggest simply installing the package (as long as it's an ubuntu package), and trust the packagers to have configured it correctly (bugzilla.ubuntu.org if not).  If you don't have an ubuntu package you will have to go from source, in which case you can configure with --prefix set.

L.

---

### Post by GOwin on 2005-05-12
i was instructed that if gnokii is installed somewhere else, i'd

>  if you want to change to another directory, you better understand how to 
    read source of /path_to_source_of_playsms/bin/* files written in bash script


I'm afraid the consequences to running the program would be worse for me.

Could I fool the application by creating symlinks at the expected location pointing to where gnokii is installed?

---

