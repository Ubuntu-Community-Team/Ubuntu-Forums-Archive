---
title: "gtk headers"
date: 2006-08-28
forum: General Help
---

### Post by captainquack on 2006-08-28
For my life I seem unable to install the gtk headers. I cannot install them from gtk.org because one of the dependencies, atk, will not configure. Every time I try, it gives me two errors. First, it says:

*** 'pkg-config --modversion glib-2.0' returned 2.12.2, but GLIB (2.10.3)
*** was found!

and then:

*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

I installed glib 2.12.2 previously from gtk.org.

I also tried downloading the libgtk2.0-dev package from this website. However, it said that the dependency on libgtk2.0-0 was unresolvable. Indeed, it will not let my install libgtk2.0-0.

Does anyone know what I am doing wrong?

---

### Post by hw-tph on 2006-08-28
First off a word of warning: Replacing core desktop libraries such as GTK with ones built from source could make your Ubuntu/Gnome desktop unusable.

Now, the development packages in Ubuntu provide the headers files and associated tools required to build from source. Your problem seems to be the mixed environment - some files come from the Ubuntu repositories (GLIB 2.0 version is 2.10.3) while others come from your locally built software.

If you want to test and try out some stuff from source I suggest you set up a separate directory hierarchy, say in /usr/local/mysoft/ (use --prefix=/usr/local/mysoft for most packages), to avoid interfering with your Ubuntu system. You can then install locally built software there (and set $LD_LIBRARY_PATH as necessary to run the programs.

To install Ubuntu's own packages (including the development packages) you should use the apt-get, aptitude or synaptic tools. They can and will resolve most dependancy issues. **sudo aptitude install libgtk2.0-dev** will for example install the GTK header files and also any development package that libgtk2.0-dev depends on.

---

### Post by captainquack on 2006-08-28
Thank you! I'll try that...

---

