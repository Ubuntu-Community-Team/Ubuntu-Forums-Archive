---
title: "Installing RealVNC 4.1 Enterprise Edition"
date: 2005-09-15
forum: General Help
---

### Post by jwegan on 2005-09-15
I'm trying to install RealVNC 4.1 Enterprise Edition.
I downloaded the tar file and ran the vncinstall script and installed it to my /usr/local/bin/ directory.

I then tried running 'vncconfig' (or any of the other executables for that matter) but I get the error
vncconfig: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I've tried doing apt-get install libstdc++6 and apt-get install libc6 but with no success.

Any suggestions?

---

### Post by jwegan on 2005-09-15
nvm i fixed it with 
apt-get install libstdc++2.10-glibc2.2

---

