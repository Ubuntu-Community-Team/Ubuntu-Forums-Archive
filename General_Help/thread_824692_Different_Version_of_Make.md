---
title: "Different Version of Make"
date: 2008-06-10
forum: General Help
---

### Post by Black Mage on 2008-06-10
Just a question, are there different versions of make? And if so, how do I get the other versions?

---

### Post by HalPomeranz on 2008-06-10
Linux systems in general ship with what's commonly referred to as "GNU make", which is the version of make created by the Free Software Foundation.  It's the widely used "de facto standard" version of make required to compile most Open Source software.  It has functionality and extensions not present in many older versions of make.

Other operating systems may ship with different flavors of make (typically derived from older sources) that are not compatible with GNU make in many respects.  The various BSD flavors generally ship with a version of make derived from the original BSD make program (aka "Berkeley make"), Sun has their own version of make that probably at one time derived from BSD make but which now has its own specific functionality, etc.

As for obtaining the alternate versions of make, I guess you'd have to get the source code from the appropriate operating system repositories and try to build it on Linux.  I'm guessing that would be something of a chore, since the code probably assumes the presence of header files and libraries that are different from the standard Linux install.  

I'd say you're probably better off trying to make whatever code you have work with GNU make instead of trying to revert to some other make version.  GNU make does look like it's going to become the standard going forward.

---

