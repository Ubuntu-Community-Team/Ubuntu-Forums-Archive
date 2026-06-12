---
title: "installing to opt"
date: 2008-05-02
forum: General Help
---

### Post by discontentment68 on 2008-05-02
I've been using linux for a few years now, yet i'm still not sure how to configure my environment.  If a makefile has path variables, how do i set these correctly so that my compiled software is put in the opt directory?

relevant makefile portion for *make install*:
```
install:
	$(MAKE) -C src $(@)
	install -m 755 $(SCRIPTS) $(DESTDIR)$(sbindir)
	install -d $(DESTDIR)$(mandir)
	install -m 644 ./manpages/* $(DESTDIR)$(mandir)

```

A more general question relates to the general usage of opt.  Should all the necessary libraries also be installed to the opt directory, say in opt/lib?  I wanted opt to have all the source i needed to build non package software.

-Dave

---

### Post by zvacet on 2008-05-02
[Here]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by discontentment68 on 2008-05-02
I've built and installed software before.  I've compiled even the software in question yet I've never put things in opt.

The problem is that there is no *configure* script.  Does the  configure script check for dependencies and set variables?  When running it in the past to build software i remember that it outputs a whole lot of information regarding dependencies and environment variables.  

So running *./configure --PREFIX=/opt* changes these?

---

### Post by zvacet on 2008-05-02
Yes ./configure is checking that you have all you need to compile,but adding prefix /opt you are telling where you want to install package. What install file say?

---

### Post by discontentment68 on 2008-05-02
The README and the INSTALL files just say to run make and then make install.

---

### Post by discontentment68 on 2008-05-03
Ok, some stuff i didn't realize about using *make*.  Apparently variales may be set to use in the Makefile from the command line.
So, running: ```
 sudo make install DESTDIR=/opt 
``` will set the install directory to opt.  You would add variable assignments for sbindir and mandir ... 

NOTE:
After reading some more, I changed my mind about installing to /opt/local/ and i think I'd rather not have to change paths to make things work correctly.
The default directory for compiled (non-distro package) software is /usr/local/.  There is where paths default for that stuff.  So there is an sbin, a man, a share, a bin, .... in the /usr/local.  Opt is generally used for packages (including compiled packages) that don't follow a standard unix filesystem structure.

---

