---
title: "Intel Core Duo"
date: 2007-06-06
forum: General Help
---

### Post by FRuMMaGe on 2007-06-06
How do I check whether or not Ubuntu is using both cores on my laptop?  SOme people have been saying it's only using 1 core.

Also, my graphics card was fine a day ago, but now I think the drivers are uninstalled.  I know this because when i run the 3D screensavers, there is a LOT of lag. it's a 945G integrated graphics card.

Also, I can't actually choose 1280x1024 resolution like the monitor says it can go.

Here's the specs of my laptop:
2048 MB of RAM
160 GB SATA Hard Drive
Dvd Multiburner
Integrated 945G Graphics
54G Wireless LAN

etc.

It's all intel.  Any help would be appreciated.

---

### Post by robrmd9 on 2007-06-06
To check if both cores are detected by the kernel, do ```
cat /proc/cpuinfo |grep processor
```.  You should see something like ```
processor: 0
processor: 1
```

If you only see one, then you are probably not using the correct kernel.  Try the generic kernel (linux-image-generic), although Edgy and Feisty should detect the correct kernel to use during installation.

---

### Post by eggdeng on 2007-06-06
Use Add to Panel to add a System monitor icon to your panel. Open it to see your processor(s) on the resources tab. If you only see one, check your kernel version using the command ```
uname -a
``` You will see a string with something like  ```
 2.6.15-27-686 #1 SMP 
``` The SMP kernel is the one you need. If you haven't got it already, you can get it with ```
apt-get install linux-image-686-smp
``` Remember that kernel updates will break your graphics drivers, you have to reinstall. Also remember you can revert to an older kernel by choosing it in the grub boot menu or editing /boot/grub/menu.lst.

---

### Post by mcduck on 2007-06-06
> **eggdeng said:**
> Use Add to Panel to add a System monitor icon to your panel. Open it to see your processor(s) on the resources tab. If you only see one, check your kernel version using the command ```
uname -a
``` You will see a string with something like  ```
 2.6.15-27-686 #1 SMP 
``` The SMP kernel is the one you need. If you haven't got it already, you can get it with ```
apt-get install linux-image-686-smp
``` Remember that kernel updates will break your graphics drivers, you have to reinstall. Also remember you can revert to an older kernel by choosing it in the grub boot menu or editing /boot/grub/menu.lst.
There has not been a separate SMP/686/K7 kernels since Dapper, both Edgy and Feisty have generic kernel supporting all of those CPU's..

(yes, there are still such packages in Synaptic, but they are just empty packages pointing to the generic kernel, provided for those upgrading from older Ubuntu versions)

---

### Post by eggdeng on 2007-06-06
Thanks for the correction. I'll let the  post stand for anyone using Dapper.

---

### Post by FRuMMaGe on 2007-06-10
> **eggdeng said:**
> Use Add to Panel to add a System monitor icon to your panel. Open it to see your processor(s) on the resources tab. If you only see one, check your kernel version using the command ```
uname -a
``` You will see a string with something like  ```
 2.6.15-27-686 #1 SMP 
``` The SMP kernel is the one you need. If you haven't got it already, you can get it with ```
apt-get install linux-image-686-smp
``` Remember that kernel updates will break your graphics drivers, you have to reinstall. Also remember you can revert to an older kernel by choosing it in the grub boot menu or editing /boot/grub/menu.lst.

says it cant find it :(

---

### Post by eggdeng on 2007-06-10
You mean apt-get didn't find an SMP kernel? Can you post what version of ubuntu you are using. if you're not sure, go to System -> Help -> System Documentation and you will see it (6.06, 6.10 or 7.04). And post the output of ```
uname -a
``` or did you get a command not found with that?

---

### Post by robrmd9 on 2007-06-10
It's possible he put down the wrong package (or perhaps they've been renamed since Dapper).  In Feisty they are linux-image-686 and linux-686-smp

Try:

```
sudo apt-get install linux-image-generic
```

The generic kernel will detect and use both cores.

---

### Post by FRuMMaGe on 2007-06-11
Can't find that either.

I'm using Dapper 6.06, and my uname -a is:

```
Linux frummage-laptop 2.6.15-28-386 #1 PREEMPT Thu May 10 09:45:43 UTC 2007 i686 GNU/Linux
```

---

### Post by mcduck on 2007-06-11
> **FRuMMaGe said:**
> Can't find that either.

I'm using Dapper 6.06, and my uname -a is:

```
Linux frummage-laptop 2.6.15-28-386 #1 PREEMPT Thu May 10 09:45:43 UTC 2007 i686 GNU/Linux
```
What you need is the 686 SMP kernel. Install the 'linux-686-smp' package, that will install everything needed, and also makes sure your kernel updates work correctly.

'sudo apt-get install linux-686-smp' should do the trick.

---

### Post by eggdeng on 2007-06-11
OK, I got the name of the package wrong. This should work for you.
```
sudo apt-get install linux-686-smp
```

---

### Post by FRuMMaGe on 2007-06-12
> **eggdeng said:**
> OK, I got the name of the package wrong. This should work for you.
```
sudo apt-get install linux-686-smp
```

Got it.  It works now!

A little bit of trouble reinstalling my wireless drivers, but now im back and fully operational! Thanks!

---

