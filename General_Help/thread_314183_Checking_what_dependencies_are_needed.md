---
title: "Checking what dependencies are needed"
date: 2006-12-07
forum: General Help
---

### Post by b3n87 on 2006-12-07
Hello, i keep finding new programs on the internet that i wont to install, so i download the source and run ./configure, make, make install, or what ever is needed. but half the time it comes up with errors, im guessing its because of an dependencies issues

is there a command you can type to check what dependencies are needed for that source?

Thanks in advance

Ben

---

### Post by nikhilk on 2006-12-07
Unfortunately the only ways (that I know of) to find out dependencies for a source tarball are:
1. The "configure" script itself
2. The documentation provided with the source or on the maintainer's website (if any)

That is why package management systems (RPM, DEB etc) make life simpler.

---

