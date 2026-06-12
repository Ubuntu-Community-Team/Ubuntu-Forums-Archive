---
title: "What is /etc/dpkg/dpkg.cfg.d/multiarch ?"
date: 2013-11-15
forum: General Help
---

### Post by vasa1 on 2013-11-15
It has been mentioned here: [http://ubuntuforums.org/showthread.php?t=2187957&p=12848203#post12848203](http://ubuntuforums.org/showthread.php?t=2187957&p=12848203#post12848203) but my /etc/dpkg/dpkg.cfg.d/ folder is empty. My OS is Lubuntu 13.10.

---

### Post by fantab on 2013-11-15
No idea. I have that folder empty in both 'Saucy' and 'Trusty', Ubuntu. However, I can double click on .deb files and they quite cleanly install/open with 'Software Center'.

---

### Post by vasa1 on 2013-11-15
The context was difficulty installing 32-bit software on a 64-bit system.

"apt-cache show multiarch support" has this:> Description-en: Transitional package to ensure multiarch compatibility
 This is a transitional package used to ensure multiarch support is present
 in ld.so before unpacking libraries to the multiarch directories.  It can
 be removed once nothing on the system depends on it.
Oh, well ...

---

### Post by vasa1 on 2013-11-15
[This comment]("http://askubuntu.com/questions/238006/why-does-my-64-bit-system-look-for-32-bit-repos/238043#comment296714_238043") has:
> I recommend running *dpkg --print-foreign-architectures* rather than *catting /etc/dpkg/dpkg.cfg.d/multiarch*. It doesn't exist after 12.04.
and running the recommended command gives all of```
[05:33 PM] ~ $ dpkg --print-foreign-architectures
i386
```

---

