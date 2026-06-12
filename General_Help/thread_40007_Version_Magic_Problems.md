---
title: "Version Magic Problems"
date: 2005-06-07
forum: General Help
---

### Post by sgtstadanko on 2005-06-07
Ok....i've managed to screw something up with my headers. I am running kernel 2.6.10-5-amd64-generic and whenever I try to compile any module and insert, it fails with invalid format and dmesg says " version magic '2.6.10-5-amd64-generic gcc-3.4' should be '2.6.10-5-amd64-generic gcc-3.3'". I have tried uninstalling an reinstalling the linux-headers packages but keep getting the same error. I have the following linux-header packages installed:

linux-headers-2.6.10-5
linux-headers-2.6.10-5-amd64-generic
linux-headers-2.6.10-5-amd64-k8

What am i missing here?

thanks,
bill

---

### Post by geoffreyprewett on 2005-06-11
I just got finished fixing this problem on my Gentoo box.  In my case, the problem was caused by switching from gcc 3.2.3 to 3.3, then recompiling my kernel, but not re-running lilo.  My guess at what happened was that the new image did not overwrite the old image, but was written to a new location.  Lilo apparently stores actual disk locations, so it needs to be re-run.  (This *ought* to motivate me to switch to GRUB).  I'm sure this could also manifest itself as modules that don't get loaded but work anyway (if you switched your kernel to use something as a module, lilo would load the old kernel that had it compiled in)

I don't know if Ubuntu uses lilo, though, so this might not solve your problem.

---

