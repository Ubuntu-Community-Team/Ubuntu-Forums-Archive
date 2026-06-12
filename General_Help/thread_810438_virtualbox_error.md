---
title: "virtualbox error"
date: 2008-05-28
forum: General Help
---

### Post by hamzamusa on 2008-05-28
hi 

am trying to make the virtualbox run , but got stuck with the message : 

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

so i installed :
```
sudo apt-get install virtualbox-ose-modules-generic
```

also i can't start the " vboxdrv " using this :
```
sudo modprobe vboxdrv
```


though something the message dosn't even change , even when i added this user group to " vboxusers " .

am on Ubunto 8.04 .

What's went wrong and how can i fix this issue ?

---

### Post by sizzam on 2008-05-28
Does /etc/init.d/vboxdrv exist?   If so, try this from a command prompt:
```
sudo /etc/init.d/vboxdrv setup
```

Then relaunch VirtualBox to see if it works.

---

### Post by hamzamusa on 2008-05-28
Trying This :
> sudo depmod -a
sudo /etc/init.d/vboxdrv start

The vboxdrv is worked , though this is the new error now 

> 
No suitable module for running kernel found.


running status : 
>  
sudo /etc/init.d/vboxdrv status
VirtualBox kernel module is not loaded.

working on it , any suggestions ?

---

### Post by sizzam on 2008-05-28
I believe that it will build a suitable module for the kernel with this command:

```
sudo /etc/init.d/vboxdrv setup
```

You might need to install the kernel headers and C compiler first if you don't already have it:

```
sudo apt-get install kernel-package build-essential
```

---

### Post by hamzamusa on 2008-05-28
> sudo /etc/init.d/vboxdrv setup

comes back with this message :

> Usage: /etc/init.d/vboxdrv {start|stop|restart|status}


though i installed the kernel headers , rebooted and still has the same issue .

> No suitable module for running kernel found.

---

### Post by sizzam on 2008-05-28
Ahh, ok.  I'm not using the version from the repositories.   The repository version is OSE ([Open Source Edition]("http://www.virtualbox.org/wiki/Editions")), which doesn't have USB support and a few other features.

I installed with these steps:

First, I got supporting packages:
```
sudo apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential
```

Then I downloaded the DEB file from [ VirtualBox's website]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") and installed it with:
```
sudo dpkg -i virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb
```

I then added my user to the vboxusers group, logged out, and back in.

Note that if you are going to try this route I would recommend removing all the VirtualBox packages that were installed via the repos first.

***** Update** - if you just doubleclick on the DEB file to install it, it should automatically find all the dependencies it needs.

---

### Post by G-Dawg on 2008-05-28
Thanks sizzam I also had the non-ose version and your solution worked for me.  Appreciated.

---

### Post by Benbow on 2008-05-28
Can I ask you to explain how to find the Deb file on the vb website. Sorry to chip into your posting, hamzamusa.

---

### Post by sizzam on 2008-05-28
> **Benbow said:**
> Can I ask you to explain how to find the Deb file on the vb website. Sorry to chip into your posting, hamzamusa.

Go to [this page]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"), choose 'Ubuntu 8.04 x86' for Platform (assuming you are using 32 bit Hardy Heron), check the box if you agree to the license agreement, then click Continue.

---

### Post by hamzamusa on 2008-05-28
working on [Xen]("http://www.xensource.com/xen") , on the other pc ( dreamlinux ) , 

removing the Virtualbox-OSE and installing the other one with the supported packages .

back soon as i tested it out .

Benbow , it's ok , was a cool discussion though .

thanks alot sizzam for the great help

---

### Post by hamzamusa on 2008-05-28
Working Perfectly   now ,  The one u suggested from Sun . 

Thank You Sizzam :D

---

