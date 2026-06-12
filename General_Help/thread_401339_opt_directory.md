---
title: "opt directory"
date: 2007-04-04
forum: General Help
---

### Post by Mateo on 2007-04-04
I'd like to know what the opt directory is for.

also, if anyone has a link explaining what all of the different directory types are for, that would be great.

thanks.

---

### Post by cmost on 2007-04-04
A quick Google search netted hundreds of results.  Try here.

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by Mateo on 2007-04-04
thanks, interesting link. but it doesn't say what the opt directory is for.

---

### Post by roelpeeters on 2007-04-04
Generally speaking the opt directory is used for applications that are installed by the user in addition (by hand). If I am not mistaken opt is a abbreviation for optional. When you download a tarball you can install it in the opt dir, and then create symlinks in the /usr/bin directory that point to the executables in the opt directory.

---

### Post by dreadlord_chris on 2007-04-04
> **Mateo said:**
> I'd like to know what the opt directory is for.

also, if anyone has a link explaining what all of the different directory types are for, that would be great.

thanks.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

> 
/opt/	Add-on application software packages.


basically what roelpeeters said....

---

