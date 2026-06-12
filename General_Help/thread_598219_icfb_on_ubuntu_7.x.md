---
title: "icfb on ubuntu 7.x"
date: 2007-10-31
forum: General Help
---

### Post by redhavoc on 2007-10-31
Hello,
   I want to run a fairly old application which is not open-source. I have successfully run it on quite a few distributions which included glibc 2.4 or older. In order to run this app (its called icfb and its a CAD tool), I need to set LD_ASSUME_KERNEL to 2.4 and also set LD_LIBRARY_PATH to the usual library directories.
   The problem comes in new distros, and I have tried, SUSE 10.3, ubuntu 7.04, RHEL/CENTOS 5, Gentoo 2007.0. All those distros use glibc 2.5 or newer and for some reason the application freezes at a point. It does not crash ... it seems thats its waiting for certain things to happen, which never happen. There is no cpu activity from this process or any of its child processes. So I searched the web and forums and people suggested recompiling glibc in my distro with an option to include LinuxThreads. From what I understand LinuxThreads is an old kernel thing and that's why I'm using LD_ASSUME_KERNEL.
   Anyone has any suggestions on how to get LinuxThreads in my glibc. Does this actually sound like a viable solution. This icfb software was designed for RHEL 2 and 3. They have extended their support to RHEL 4 but they are not going further than that. 
   If you people have any comments or ideas please let me kniow.

Thanks

---

