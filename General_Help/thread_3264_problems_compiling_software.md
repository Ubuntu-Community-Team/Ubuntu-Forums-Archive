---
title: "problems compiling software"
date: 2004-11-04
forum: General Help
---

### Post by elempoimen on 2004-11-04
I'm trying to compile a package.  The dependencies are all met--I've checked and rechecked.  I have every version of libstdc++-dev available on the ubuntu servers installed.  Yet, I get this error:

Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similiar to libstd++-dev.

Help?  I can't install this package via apt-get because is says that it cannot meet the dependencies.  (the problem is the custom ubuntu versions--the version numbers of the ubuntu versions exceed those required by the package...so this should not be a problem.)

---

### Post by az on 2004-11-04
Install the package named build-essential

---

### Post by elempoimen on 2004-11-04
beautiful!  thanks!  now I get this error:

Can't find X includes. Please check your installation and add the correct paths!

What next?

---

