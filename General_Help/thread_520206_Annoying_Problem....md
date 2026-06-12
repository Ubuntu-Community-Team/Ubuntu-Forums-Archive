---
title: "Annoying Problem..."
date: 2007-08-07
forum: General Help
---

### Post by DMXell on 2007-08-07
Okay, so I was installing some dependencies for Gimp 2.3.19 (libgtk2.0-bin, libgtk2.0-common and libgtk2.0-0_2.10.14-0ubuntu3_i386 mainly) and now everytime I do anything with the synaptic package manager I get the following error:

E: libgtk2.0-bin: subprocess post-installation script returned error exit status 127

Any idea how to fix it? (If I remove any of the installed packages many core components to Ubuntu will be removed). As a side note, of the three packs I named, I believe only the GTK-common one installed, or maybe the bin. Two of the three gave me errors when they were installing.

Thanks for any help in advance!

---

### Post by Immolatus on 2007-08-07
Sudo apt-get install -f

in a terminal.

---

### Post by DMXell on 2007-08-07
I've already tried that, it doesn't work. Here's the whole message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwavpack1 wesnoth-server ladcca2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libgtk2.0-bin (2.10.14-0ubuntu3) ...
Updating the IM modules list for GTK+-2.10.0.../usr/bin/gtk-query-immodules-2.0: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory
dpkg: error processing libgtk2.0-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by DMXell on 2007-08-08
Can anyone help me?

---

### Post by DMXell on 2007-08-09
Bump...

---

