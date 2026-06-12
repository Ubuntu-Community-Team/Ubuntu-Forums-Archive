---
title: "Ubuntu error of apt-get 4ever?"
date: 2007-02-19
forum: General Help
---

### Post by psychok9 on 2007-02-19
After i try to install oss-linux_v4.0rc9-999_i386.deb for the 1st time... i get an error that tell me that i need "build-essential".
After i have installed... i get this error... always! "E: Il pacchetto oss-linux deve essere reinstallato, ma non si riesce a trovare un archivio per esso."
(english: The package oss-linux can't reinstalled, but don't found an archive for it).

What's wrong!? Why i can't remedy this problem?

I'm going crazy but i can't solve this problem... :(

p.s. after this error, if i click on oss-linux_v4.0rc9-999_i386.deb, an window tell me that: the package could be damaged or i don't have the open permission on this file. check file permission.

---

### Post by phidia on 2007-02-19
I'm not sure if this is the solution for your problem but you could try this:
> sudo dpkg -i oss-linux_v4.0rc9-999_i386.deb 

---

### Post by psychok9 on 2007-02-19
LoL

After many try... (installing with regparm and install.sh... and crash, removed file from /var/lib/dpkg/info... etc... i tryed your line sudo dpkg -i oss-linux_v4.0rc9-999_i386.deb and maybe WORK!
Thank you very much

---

