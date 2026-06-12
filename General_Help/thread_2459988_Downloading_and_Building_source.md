---
title: "Downloading and Building source"
date: 2021-03-30
forum: General Help
---

### Post by cparke on 2021-03-30
I need a newer version of a package than Ubuntu has provided through backporting for my version (16.04 LTS), and I need it on i386 architecture.  So of course, I have to download the source and build it!

This is the package I need: [https://packages.ubuntu.com/groovy/libmanette-0.2-dev](https://packages.ubuntu.com/groovy/libmanette-0.2-dev)

My question is: What's up with the 'Debian' source download also listed?  Looking at it, it seems like patches or something newer coming from the upstream.  If so, how do I combine these to make the proper build?

---

### Post by HermanAB on 2021-03-31
You could look at this: [https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html](https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html)

Specifically "Install The GCC Compiler"

Once the compile evironment is OK, just make the project and see what it complains about.

---

### Post by Impavidus on 2021-03-31
Keep in mind that 16.04 will reach end of life next month. Support for 32 bit is ending too.

---

### Post by HermanAB on 2021-03-31
Note that as in my guide linked above, rather make a virtual machine and work in that, then once it is working, turn automatic updates off.  In that way you are making the system hardware and software independent and it will then keep working as long as you need it.

---

### Post by cparke on 2021-04-03
> **HermanAB said:**
> You could look at this: [https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html](https://www.aeronetworks.ca/2018/06/compile-latest-gstreamer-from-git.html)

Specifically "Install The GCC Compiler"

Once the compile evironment is OK, just make the project and see what it complains about.
Yes, that article describes a lot of the same issues and complications that I am going through as well.

However, it doesn't explain what the 'debian' source tarball is or how to use it.  It looks like this file represents all the fixes and adjustments needed to get the original package to work on the target system.  But there is no instructions in it on how to use it!

---

