---
title: "how do I compile programs, use checkinstall, and have it not overwrite other files?"
date: 2007-07-29
forum: General Help
---

### Post by harty83 on 2007-07-29
When ever I compile a program, make, and then use checkinstall to make a deb, checkinstall and/or the configure script includes files such as gcc.  When I go to install the deb, it wants to overwrite those files.  That's not a huge deal except when I go to uninstall the compiled program and it removes files such as gcc!  Then I have to go and reinstall all the debs that originally included the overwritten files.

Please enlighten me as how to prevent this.  

Thanks!!

---

### Post by dando80 on 2007-07-30
Don't quite get what you are saying. Checkinstall will not overwrite any files unless they are from an older version of the same package. There is no way it should be overwriting files belonging to other packages. Could you explain in a little more detail with an example?

---

### Post by harty83 on 2007-07-30
> **dando80 said:**
> Don't quite get what you are saying. Checkinstall will not overwrite any files unless they are from an older version of the same package. There is no way it should be overwriting files belonging to other packages. Could you explain in a little more detail with an example?

Sure.  I was compiling gnucash 2.2.  Checkinstalled included files such as /usr/bin/gcc, /usr/bin/nm, /usr/bin/ld, and a bunch of libraries that are included in packages such as gcc, binutils, etc.  So, dpkg gives errors of course when trying to install unless the option --force-overwrite is given.  But then, when I go to uninstall gnucash (which happened on an other machine), it deleted /usr/bin/gcc, etc and I had to reinstall all those programs.  

I ended finding all of the files checkinstall included that were in other programs and excluded them by ```
checkinstall --exclude "all the file names here"
```

It worked but was time consuming and a pain.

Does that help clear things up?

Thanks!
Alan

---

### Post by kodoku on 2007-07-30
When you use checkinstall, the deb that is generated should have already been installed (if you watch the progress, it does through "Building Debian Package" and then "Installing Debian Package".  You shouldn't have to install it again.

---

### Post by harty83 on 2007-07-30
> **kodoku said:**
> When you use checkinstall, the deb that is generated should have already been installed (if you watch the progress, it does through "Building Debian Package" and then "Installing Debian Package".  You shouldn't have to install it again.

Checkinstall uses dpkg to actually install the deb file it creates.  So if the deb includes files that are in other packages, it will fail when installing with the error that the particular file is already in another package.  After this, you can either manually install the deb with ```
dpkg -i --force-overwrite packagename.deb
``` or you can do this when using checkinstall ```
checkinstall --dpkgflags "--force-overwrite"
```  Either way, files are getting overwritten which then still presents the same problem.  

I do not want checkinstall to include in the deb file it creates files that are already included in other packages.  This is the problem I'm having.

Thanks!

---

