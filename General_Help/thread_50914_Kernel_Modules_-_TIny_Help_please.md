---
title: "Kernel Modules - TIny Help please"
date: 2005-07-21
forum: General Help
---

### Post by gwon on 2005-07-21
Hey,

I've just compiled some drivers for my wireless card. Everything works brilliantly, the only problem is that every time I restart my machine, I have to cd to the directory I compiled the modules in and run insmod for the modules.

I'm totally stuck as to how to get them to load on boot.

I have four .ko files that I have compiled, and I'd like them to load each boot without any help from me.

Any help would be greatly appreciated.

---

### Post by az on 2005-07-21
#  /etc/modules:  kernel  modules to load at boot time.  # # This
file contains the names of kernel modules that should be loaded #
at boot time, one per line. Lines beginning with "#" are ignored.

Put them (the names, one per line, in /etc/modules)

---

### Post by gwon on 2005-07-22
where should the modules be or can I insert the full path?

Should I include the ".ko" part of the file name?

---

### Post by az on 2005-07-22
If the modules were made properly, they are installed to /lib/modules/(kernel)/... and you do not need to tell it the path, just the module name, withouth the .ko  

Look at what is in there now for an example.


What modules are we talking about?

---

