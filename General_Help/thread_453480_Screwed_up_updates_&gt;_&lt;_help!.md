---
title: "Screwed up updates &gt;_&lt; help!"
date: 2007-05-24
forum: General Help
---

### Post by Fireblend on 2007-05-24
Hey. Yesterday I was trying to install a package but I decided to close the window while it was installing it and I guess that screwed up the whole updates/install system.

Whenever I try to update, I get:

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.'

lg3d-jdk was the package I was trying to install before, so I guess since I closed it in the middle of instalation it screwed it up. So I download the package again to install it and the remove it, but when I open GDebi or whatever it's called, I get:

> Could not open 'lg3d-jdk1.6.0_i686.deb

The Package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

It's definitely not corrupted, I download it three times now. And I'm admin.

So I'm stuck right now. What to do?

---

### Post by jamesjtucker on 2007-05-24
I would try to run the install from the command line:
dpkg -i lg3d-jdk1.6.0_i686.deb
If that fails, it may give you some output to fix it.  let us know.

---

