---
title: "Installation of old version of ns2"
date: 2007-03-30
forum: General Help
---

### Post by t_anjan on 2007-03-30
I've got to install ns2.1b6 on my Edgy for a college project. ns2 is a network simulator. I know for sure that that particular version installs without a hitch on Red Hat 7.3 . But I get errors when trying to install it on Edgy.

Here is the link to the tar: [http://www.isi.edu/nsnam/dist/ns-allinone-2.1b6a.tar.gz](http://www.isi.edu/nsnam/dist/ns-allinone-2.1b6a.tar.gz)

It is an all-in-one package, in the sense that it contains all the dependencies in the tar. The installer script takes care of installing the dependencies. The script throws up errors that I can't understand. But the very same script works flawlessly on Red Hat 7.3 . Can someone try out the installation and tell me what is to be done?

The installer script completes the installation of the first two packages: tcl and tk. When it starts to 'make' the next package 'tclcl', it gives the following error:

```
tclcl-mappings.h: In static member function &#8216;static int TclObjectHelper<T>::dispatch_(void*, Tcl_Interp*, int, char**)&#8217;:
tclcl-mappings.h:51: error: incomplete type &#8216;Tcl&#8217; used in nested name specifier
tclcl-mappings.h:52: error: invalid use of undefined type &#8216;struct Tcl&#8217;
tclcl-mappings.h:41: error: forward declaration of &#8216;struct Tcl&#8217;
tclcl-mappings.h:57: error: invalid use of undefined type &#8216;struct Tcl&#8217;
tclcl-mappings.h:41: error: forward declaration of &#8216;struct Tcl&#8217;
make: *** [Tcl.o] Error 1
tclcl-1.0b9 make failed! Exiting ...
See http://www-mash.CS.Berkeley.EDU/ns/ns-problems.html for problems
```

I would be grateful for any help with this. What is there in Red Hat 7.3 that is not there in Ubuntu Edgy?

---

### Post by dragonx on 2008-01-29
I have the same problem with mustafa package (ns2.1b9 with uwb)
I need help

---

