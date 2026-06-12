---
title: "virtual box?"
date: 2008-05-08
forum: General Help
---

### Post by Dunover on 2008-05-08
I am wanting to use the new version of ubuntu but look at the bugs i see a bug report for VBox? am getting that error when trying to run it...I really like to use this...has there been a fix posted? If so I have not seen it yet.

thanks!
Corisa

---

### Post by p_quarles on 2008-05-08
What is the error you are getting?

---

### Post by Dunover on 2008-05-08
This is the error it seems to be the one posted on the bugs list??

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by p_quarles on 2008-05-08
> **Dunover said:**
> This is the error it seems to be the one posted on the bugs list??

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
Run the following command in a terminal. That should fix the problem.
```
sudo apt-get install virtualbox-ose-modules-'uname -a'
```
You will need to reboot following this command, so the new module can be recognized by the kernel.

---

### Post by Dunover on 2008-05-08
it gave me this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose-modules-uname -a
xxx@xxx-desktop:~$

---

### Post by DoktorSeven on 2008-05-08
uname -a should be `uname -r`.

The "quotes" around uname -r, also,  should be "backticks", i.e. ` (above tab on US keyboards, not sure where to find it otherwise), not apostrophies or real quotes.

This tells it to append the output of the command inside the backticks to the command you're running (i.e. the current kernel).

---

### Post by Dunover on 2008-05-09
that fixed it ...thanks!
Cori

---

### Post by swoosietole7 on 2011-01-16
> **Dunover said:**
> I am wanting to use the new [[COLOR=#000000]version[/COLOR]](http://www.conversion-guides.com/yuv-conversion-guide/yuv-to-h263-guide.html) of ubuntu but look at the bugs i see a bug report for VBox? am getting that error when trying to run it...I really like to use this...has there been a fix posted? If so I have not seen it yet.thanks!CorisaIt is exactly what I need, Now I understand more about it, Thanks for your analysis! It's very detailed.

---

