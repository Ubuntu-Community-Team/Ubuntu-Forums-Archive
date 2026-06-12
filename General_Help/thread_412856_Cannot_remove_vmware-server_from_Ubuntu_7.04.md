---
title: "Cannot remove vmware-server from Ubuntu 7.04"
date: 2007-04-18
forum: General Help
---

### Post by jaywatkins on 2007-04-18
Hello,

I have recently upgraded my copy of 6.10 to 7.04 Beta.  Everything went fine, except for VMWare Server, it will not run.   I was going to try and remove it, but apt-get/adept cannot find the package in it's repository (I guess).  

sudo apt-get remove vmware-server
sudo apt-get remove vmware-server-1.0.2-39867

^ Does not produce any results ^  

How can I manually remove vmware and start fresh?

Thanks

---

### Post by xopher on 2007-04-18
> $ apt-cache search vmware-server
vmware-server-kernel-modules-2.6.20-15 - vmware-server modules for Linux (kernel 2.6.20)
vmware-server-kernel-modules - vmware-server kernel module dependency package

This is everything I found when searching for ^ vmware-server.. So there's no package for the real application in the repositories, the modules are there though, and they can be handy when installing.

You probably have to download the program from their homepage, and install it manually..

To check if you even have vmware-server installed still do a:

```
dpkg -l | grep vmware
```

That'll show every package with vmware in it's name. **ii** before the package means it's installed, **rc** that it's in your cache.

---

### Post by jaywatkins on 2007-04-18
It came back with VMWare player as being the device installed.  I removed that, and then the terminal informed of other "un-needed" packages that were still installed.  I removed them with 

sudo apt-get remove autoclean

Upon reboot, a prompt indicating that  iwas using an unsupported driver for the vmware virtual adapters has been installed.  Wait, I thought I removed it...  ???

Any ideas?

Thanks

---

### Post by beerorkid on 2007-04-18
betting you need to remove the /etc/vmware directory.  is always the case ;)

then you can try again.

[this worked for me]("http://ubuntuforums.org/showpost.php?p=2384779&postcount=52")

---

### Post by jaywatkins on 2007-04-18
No sh*t!

That did it.  Thanks!

---

### Post by veugelenw on 2007-08-06
> **beerorkid said:**
> betting you need to remove the /etc/vmware directory.  is always the case ;)

then you can try again.

[this worked for me]("http://ubuntuforums.org/showpost.php?p=2384779&postcount=52")

This also works for me, thx!

---

### Post by danshirah on 2008-05-06
me as well on 8.04, thank you very much.

---

