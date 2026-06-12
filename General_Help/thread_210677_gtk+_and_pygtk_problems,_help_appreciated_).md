---
title: "gtk+ and pygtk problems, help appreciated :)"
date: 2006-07-07
forum: General Help
---

### Post by litemotiv on 2006-07-07
dear all,

having switched over to ubuntu completely 2 weeks ago, i have now started investigating the wonderful world of finding and compiling interesting new programs. as of yet i've found several programs that require gtk+2.4 and pygtk2.0, though i keep running into problems trying to compile them.

these are the error messages i often get when compiling:

```

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pygtk-2.0' found

```

according to synaptic, these versions are installed on my system:

libgtk2.0-0 (and it's dependencies)
The GTK+ graphical user interface library
version: 2.8.18-0ubuntu2

python2.4-gtk2 (and it's dependencies)
Python bindings for the GTK+ widget set
version:2.8.6-0ubuntu1

however, the files mentioned in the error message (gtk+-2.0.pc and pygtk-2.0.pc) don't seem to be on my system.

how could i go about trying to fix this? i can imagine it would be advisable to remove the current packages and reinstall them, in which case: how would i do this without also removing other depending applications (like amarok)? 

i've searched the ubuntu forums and google but haven't been able to find a solution yet. compiling new versions from scratch from [www.gtk.org](www.gtk.org) seems a bit too hazardous considering my limited knowledge on the subject (and fear of messing up other packages or the great running ubuntu installation as a whole). or am i maybe missing the big picture, and am i doing something wrong altogether?

thanks in advance for any help or feedback. ;)

from the netherlands,
olivier.

---

### Post by mohdridha on 2007-01-03
Similar problem to mine at [http://ubuntuforums.org/showthread.php?t=330062](http://ubuntuforums.org/showthread.php?t=330062)

---

