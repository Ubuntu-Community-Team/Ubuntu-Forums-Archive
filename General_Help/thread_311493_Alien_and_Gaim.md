---
title: "Alien and Gaim"
date: 2006-12-02
forum: General Help
---

### Post by juantovarm on 2006-12-02
Hello, i am trying to make a deb package of gaim 2 beta 5. I downloaded the rpm package and when i try to convert it with alien i got this: 
any ideas?

juan@juan-desktop:~/Desktop$ sudo alien -d gaim-2.0.0-0.beta5.fc1.i386.rpm 
Password:
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
aviso: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
warning: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc
Warning: Skipping conversion of scripts in package gaim: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
aviso: gaim-2.0.0-0.beta5.fc1.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4c292fcc

---

### Post by fragos on 2006-12-03
Don't try it.  All deb packages aren't created equal.  A deb for Ubuntu and for Debian may not be the same.  What would make a deb from alien any better.  I'm not saying it won't work just that it might not or only seem to.  Gaim is available in an ubuntu repository.

---

### Post by KuriKai on 2006-12-03
you can get gaim beta-5 from the debuntu (search google) repository

---

### Post by xopher on 2006-12-03
Or backport it yourself from Feisty with eg. prevu ;)

---

