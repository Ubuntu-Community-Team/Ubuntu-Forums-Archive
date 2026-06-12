---
title: "[SOLVED] Emesene problems"
date: 2007-07-26
forum: General Help
---

### Post by cra1g on 2007-07-26
Hey  I've got a problem. When I try to update,  i get this error:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package emesene needs to be reinstalled, but I can't find an archive for it.'

I also get this error when trying to open Synsptic Package Manager:

E: The package emesene needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)

And it wont let me reinstall emesene. Any Ideas? Thanks

Is my deb database corrupted?

---

### Post by whiskyansoda on 2008-04-15
I have the same problem!

---

### Post by whiskyansoda on 2008-04-16
READY!! HERE ARE THE ANSWER!!! Just Type Exactly this and thats all! 

sudo dpkg -r --force-depends --force-remove-reinstreq emesene


You should get this,


dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `emesene' missing, assuming package has no files currently installed.
96090 files and directories currently installed.)
Removing emesene ...


Then open and close the synaptic manager twice and thats all!

---

