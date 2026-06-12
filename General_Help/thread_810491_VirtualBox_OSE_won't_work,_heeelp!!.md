---
title: "VirtualBox OSE won't work, heeelp!!"
date: 2008-05-28
forum: General Help
---

### Post by crazyfuturamanoob on 2008-05-28
Ok, I installed VirtualBox OSE and the correct modules package.
I hve checked a million times that the modules package is the right
one by running "uname -a" in console and comparing the output to the
package's description. But when I try to run VirtualBox OSE it says:
> WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

Anyway I noticed my kernel version is 2.6.24-**17**-generic, but
the package's is 2.6.24-**16**-generic. Could that be the problem?
If it is, how to fix it? There is no packages for 17, only for 16.
What to do? How to get it working??? I really need to get it working.

---

### Post by sizzam on 2008-05-29
There is a VirtualBox module package for 2.6.17 in the repos, do you have that installed?
```
sudo apt-get install virtualbox-ose-modules-2.6.24-17-generic
```

---

