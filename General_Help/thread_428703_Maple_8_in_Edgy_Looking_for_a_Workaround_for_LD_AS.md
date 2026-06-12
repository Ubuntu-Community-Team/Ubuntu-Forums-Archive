---
title: "Maple 8 in Edgy: Looking for a Workaround for LD_ASSUME_KERNEL"
date: 2007-04-30
forum: General Help
---

### Post by Iainuki on 2007-04-30
Maple 8 has some fairly annoying bugs relating to a decision to use internal symbols from glibc that were removed in a later release of the library.  To get it to install, I had to copy the CD to my hard drive, replace the JRE included with the CD with a modern JRE, and perform an edit to the install script to comment out a a line that set LD_ASSUME_KERNEL.

However, getting the program to *run* is another matter entirely.  Again, I tried replacing the  JRE included with the installation with a modern version, specifically, 

```
sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre /usr/local/maple/jre.IBM_INTEL_LINUX
```

When I was running Debian with a 2.4 kernel, this worked.  However, on Edgy with a 2.6 kernel, I still received the same error when I tried to start xmaple:

```
/usr/local/maple/bin.IBM_INTEL_LINUX/mserver: relocation error: /usr/local/maple/bin.IBM_INTEL_LINUX/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

Maplesoft's support site suggested using LD_ASSUME_KERNEL=2.4.1 to solve this problem: [http://www.maplesoft.com/support/Faqs/Maple8/Installation/12.aspx](http://www.maplesoft.com/support/Faqs/Maple8/Installation/12.aspx).  However, setting LD_ASSUME_KERNEL breaks *everything*: basic utilities like ls stop functioning, indicating they can't find libc.so.6 and librt.so.1.  My current hypothesis is that because Edgy no longer uses linuxthreads, the modern libraries don't play well with LD_ASSUME_KERNEL.

I think if I want to get this program working, I'm going to need old libraries.  Does anyone have previous experience with LD_ASSUME_KERNEL and how to get it to work under Edgy?  Alternatively, are there any other workarounds I should look into?

---

