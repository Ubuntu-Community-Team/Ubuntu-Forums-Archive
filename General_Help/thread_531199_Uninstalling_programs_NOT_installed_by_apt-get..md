---
title: "Uninstalling programs NOT installed by apt-get."
date: 2007-08-21
forum: General Help
---

### Post by Sean K on 2007-08-21
When I installed programs from source, it is eventually done by 'make' and then 'make install,' but is there any way to UNINSTALL these programs if you no longer have the source?

When I first installed Linux I installed a whole bunch of programs from source, but never kept the source files. Is it possible for me download an "updated" source of the program I want to uninstall (from the web), and then use THAT to uninstall it? With 'make uninstall' maybe?

Secondly, how do you go about uninstalling a program if you don't have access to it's source, at all?

Thanks!

---

### Post by Delkster on 2007-08-21
> **Sean K said:**
> Secondly, how do you go about uninstalling a program if you don't have access to it's source, at all?

If you have a piece of software that you don't have the source for an that has not been installed from a deb package, you've most likely installed the software either manually by placing the contents of an archive just somewhere and then running it from there, or with an installer script. In the former case you'd just delete whatever you manually placed from wherever you placed it (in that case it's usually all in a single directory/folder so it shouldn't be difficult to find out where all the files are). In case of installer scripts, applications that come with those usually have an uninstall script somewhere as well.

As for removing applications installed from source with make, I'm not completely sure what the best approach is. You could try with a new source package, or you could see what you can find in /usr/local. The executable files are probably in /usr/local/bin and any libraries might be in /usr/local/lib/name-of-software. It might also have something in /usr/local/share/name-of-software, and potentially something in /usr/local/include/name-of-software.

For future reference, source packages can also be installed with checkinstall which first builds a simple rudimentary deb package and then installs it. That should make uninstalling simple if you remember the package name.

---

