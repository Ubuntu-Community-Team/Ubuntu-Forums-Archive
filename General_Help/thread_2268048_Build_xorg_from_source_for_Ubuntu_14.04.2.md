---
title: "Build xorg from source for Ubuntu 14.04.2"
date: 2015-03-05
forum: General Help
---

### Post by Keith_Helms on 2015-03-05
I'm trying to build xorg server from source in order to pick up a patch for bug 1220426.  I'm running Ubuntu 14.04.2 which uses the xserver stack from Utopic.

I verified I had the build dependencies met using "sudo apt-get build-dep xorg-server-lts-utopic".  That installed a bunch of packages.

I applied the patch and then tried to compile the code using "sudo fakeroot debian/rules binary".  Note: I'm just following instructions and don't fully understand what these commands are doing. <g>

Anyway, that command ran for a few minutes, spit out thousands of lines, and appeared to compile dozens or hundreds of files.  Eventually it gets to a point where it fails with the following errors:

dh_shlibdeps
sed -i 's/libgl1-mesa-glx /libgl1-mesa-glx-lts-utopic /' -i debian/xserver-xorg-core-lts-utopic.substvars
sed: can't read debian/xserver-xorg-core-lts-utopic.substvars: No such file or directory
make[1]: *** [binary-deb] Error 2

Does anyone have a suggestion on how to get around this problem?

---

