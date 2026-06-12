---
title: "[SOLVED?] &quot;Unable to load nvidia.ko&quot; at reinstall, 8.04"
date: 2008-03-23
forum: General Help
---

### Post by bobby_d on 2008-03-23
Using Ubuntu 8.04, and had the proprietary nvidia installed, everything running fine. Had to recompile the kernel, which requires reinstallation.. 

Did it a couple of times without problems, but I guess in the end it was too much mess, and attempting the reinstall resulted with "Unable to load nvidia.ko"... Additional reinstalls would fail with the same message.. 

So tried to look at this post [http://www.nvnews.net/vbulletin/showthread.php?t=80522](http://www.nvnews.net/vbulletin/showthread.php?t=80522), not much help.. 

As the dmesg was something like "disagrees about version of symbol struct_module", I suspected there were some nvidia files left on the system, which cause the compiler not to build from scratch. So I looked for all files named "nvidia" and started deleting them manually - very likely, some of these were the open drivers with ubuntu... Nevertheless that didn't help either.. 

Finally, I ran dpkg in another context, and it reported a "serious warning: files list for package 'nvidia-glx' missing, assuming package has no files currently installed" and the same for "nvidia-kernel-common".. So I tried removing these with 
dpkg -P nvidia-glx nvidia-kernel-common

dpkg reported an error "not removing linux-restricted-modules-2.6.24.12-generic depends on nvidia-kernel-common"

so finally I issued

apt-get remove linux-restricted-modules-2.6.24.12-generic

And they were (almost) gone - apt-get asked itself for "apt-get autoremove" to be ran, to remove nvidia-kernel-common...

And I believe it was after this, that it got possible to install the restricted modules again for the custom kernel (although there were some rebuilds of that kernel in between as well, which may have contriibuted).. 

Hope this helps.. :popcorn:

---

