---
title: "Intel Duo Core CPU E8400 Arch Type"
date: 2008-07-09
forum: General Help
---

### Post by whookway on 2008-07-09
Hi,
I have just installed hardy on a Shuttle with a core 2 Duo CPU E8400.  I am trying to build a driver for a 3M touch screen.  Two questions:

When I try to build I get the error No Compatible Architectures found for build.  Using uname -p I get X86_64.  The build file has i686 i586 i486 and i386, are any of these the same as X86_64?  Can I just add X86_64 to the build file?  Should I have installed a 32 bit version of the OS?

As an experiment I added X86_64 to the build file and I now get the error missing file: devfs_fs_kernel.h, should this file be on my system?  From searches it appears as if this file was removed from the install.  Can I get this file to satisfy the build?

Thank You for your help.
Will

---

