---
title: "Possible to uninstall package with 'find' and 'rm'?"
date: 2017-01-17
forum: General Help
---

### Post by peter1897 on 2017-01-17
I have installed package which i can't remove with _apt-get remove 'package-name'_ or _aptitude remove 'package-name'_. It says that the package is not installed, but it is there. Can i remove the package manually using the 'find' and 'rm' command? Something like:```
 find / -name "package-name" -exec rm -rf {} \;
```

---

### Post by deepakdeshp on 2017-01-17
Hello,
It is not possible with find command.
It would help to know which package you installed and the method to install the same.

---

### Post by peter1897 on 2017-01-17
Why it is not possible to uninstall a package with the find command?

---

### Post by Habitual on 2017-01-17
Where angels fear to tread? :)

---

### Post by howefield on 2017-01-17
> **peter1897 said:**
> Why it is not possible to uninstall a package with the find command?

It's possible but not very sensible, usually :)

What's the application and how did you install it, someone might be able to give you a better method ?

---

### Post by steeldriver on 2017-01-17
Debian/Ubuntu packages are not just collections of files - they often have pre- and/or post-installation scripts that reconfigure things

Even if they ARE just collections of files, they are not helpfully named with the package name as part of the path - so `find -name "package-name"` isn't going to be helpful - you would need to have the fileslist file for the package (from the dpkg database) - and if you've got *that*, then you may as well let apt or dpkg do the work for you

The exception would be for things that aren't really "packages" per se - such as software that you have installed from source, or from a 3rd party binary tarball

---

### Post by The Cog on 2017-01-17
> **peter1897 said:**
> Why it is not possible to uninstall a package with the find command?

Because a package is so much more than a file. It is a collection of files along with scripts for installing and removing, and lists of other packages that it requires or conflicts with. Find just might find the package file, but might also find any number of files with similar names, and certainly won't know how to remove any files that were zipped up inside the package file, or what to do to clean up afterwards.

It would help if you could tell us the version of Ubuntu you are using, and post a copy of the command you are using to remove the package along with the output from that command.
Also, how did you install the package?

---

### Post by peter1897 on 2017-01-17
Thanks, for the answers. My question is more in general if it is possible to uninstall package with 'find' and 'rm', but i guess it is not.

---

