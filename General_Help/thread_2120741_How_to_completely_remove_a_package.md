---
title: "How to completely remove a package?"
date: 2013-02-27
forum: General Help
---

### Post by Cario on 2013-02-27
I installed a package which blocked another program, but now I want to use the other program, but I can't install it because I don't think the package blocking it is completely removed. How would I make sure that it's removed?

---

### Post by JRV on 2013-02-27
```

sudo apt-get purge [PACKAGE]
sudo apt-get autoremove

```

---

### Post by Lisiano on 2013-02-27
Attempting to install a conflicting application using Apt would result in Apt trying to remove whatever application(-s) are conflicting (For example win1.4 and wine1.5, installing either one of those when the other is installed, will cause Apt to remove the other one and install the one you want). Could you please tell us what error you are getting exactly when you try to install your application?

---

### Post by Cario on 2013-03-01
The program I installed which I removed ( but I don't think got removed ) is a package called m4. When I installed it it removed VirtualBox, so when I try to install VirtualBox I get this error:
```

> sh VirtualBox-4.0.18-82821-Linux_x86.run 
Verifying archive integrity... All good.
Uncompressing VirtualBox for Linux installation......................
VirtualBox Version 4.0.18 r82821 (2012-12-18T11:37:47Z) installer
Please install the build and header files for your current Linux kernel.
The current kernel version is 3.2.0-29-generic-pae
Problems were found which would prevent VirtualBox from installing.
Please correct these problems and try again.

```

But when I install it with "apt-get install virtualbox4.1", it install but a section of it is not installing properly.


Thanks for your help,
Cario

---

### Post by efflandt on 2013-03-01
So did you do what it said and install headers for your kernal (and **dkms**, or maybe installing dkms would install your kernel headers)?

You can get a newer VirtualBox version by following Debian instructions on [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) (currently 4.2.8)

---

### Post by Cario on 2013-03-01
Yes, I installed headers and dkms and stuff, but it still isn't working. I'll try installing the newest VirtualBox version, hopefully that will work. 

Thanks,
Cario

P.S. The reason I was trying to install the older version of VirtualBox is because I thought the newest version couldn't boot floppies, but I researched it and now know that it can.

---

### Post by Cario on 2013-03-02
I tried installing the newest version of virtualbox using "apt-get install virtualbox" but the same thing happens, I get this error:
```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.2.8/source ->
                 /usr/src/vboxhost-4.2.8

DKMS: add completed.
Failed to install using DKMS, attempting to install without
Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```
I can open VirtualBox, but when I try to load one of the virtual machines it says, "Kernel driver not installed (rc=-1908)"

Thanks,
Cario

---

### Post by xp15 on 2013-03-03
I found this thread: [http://ubuntuforums.org/showthread.php?t=2081704](http://ubuntuforums.org/showthread.php?t=2081704)
very similar, and marked as solved ^^ .

Did it help?

---

### Post by Cario on 2013-03-03
I tried what the thread said and the same thing happened...

```
> sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules             
 Error! Could not locate dkms.conf file.
File:  does not exist.
                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                                                                  
Error! DKMS tree already contains: vboxhost-4.2.8
You cannot add the same module/version combo more than once.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                        
 * Look at /var/log/vbox-install.log to find out what went wrong
```

Here is what the "/var/log/vbox-install.log" file says:
```
Uninstalling modules from DKMS
Attempting to install using DKMS
Failed to install using DKMS, attempting to install without
Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

I don't know what to do. Any other ideas?

Thanks,
Cario

---

