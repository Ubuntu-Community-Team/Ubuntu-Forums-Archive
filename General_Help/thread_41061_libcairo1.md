---
title: "libcairo1"
date: 2005-06-11
forum: General Help
---

### Post by arnieboy on 2005-06-11
I am having problems upgrading mozilla-firefox through apt-get because the following package is broken:
[http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb) 
Can anybody kindly look into this and fix it?

---

### Post by cdk on 2005-06-11
yes i am having the same problem right now too

---

### Post by arnieboy on 2005-06-11
The nerim stable (unstable is fine) packages list file is also broken. apt-get is showing a MD5SUM mismatch..

---

### Post by CzarDerivative on 2005-06-11
same problem here. md5sum mismatch, and it won't let me update.

---

### Post by cdk on 2005-06-12
[QUOTE=CzarDerivative]same problem here. md5sum mismatch, and it won't let me update.[/QUOTE]
 i figured out a way around the problem

change your repo from us.archlinux.org to archlinux.org
basically the repo is messed up so if you remove all of the "us." from the repos then run an update you can install libcairo1

cheers,

---

### Post by arnieboy on 2005-06-13
[QUOTE=cdk]i figured out a way around the problem

change your repo from us.archlinux.org to archlinux.org
basically the repo is messed up so if you remove all of the "us." from the repos then run an update you can install libcairo1

cheers,[/QUOTE]

Thanks for the tip cdk. It worked! The nerim stable repository is still down though. It still shows a md5sum mismatch.

---

