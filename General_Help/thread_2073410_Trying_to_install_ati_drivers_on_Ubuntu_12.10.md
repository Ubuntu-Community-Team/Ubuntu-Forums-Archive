---
title: "Trying to install ati drivers on Ubuntu 12.10"
date: 2012-10-19
forum: General Help
---

### Post by Justsum1 on 2012-10-19
I just installed Ubuntu 12.10, and cannot install graphics card drivers. The ones in the software sources don't work, under the "propietary drivers" title. Nothing happens.

Then i downloaded the installer package from amd site, and the error message i get is the following:

----------------------
One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools.
Forcing install will disable amd hardware acceleration and may make your system unstable. Not recommended.
See usr/share/ati/fglrx-install.log for more details.
---------------------

So what tools am i missing here?? Quick help would be more than welcome!

---

### Post by timgood on 2012-10-19
You need to install the kernel headers for your version of the kernel.

Hope this helps.

---

### Post by grahammechanical on 2012-10-19
When you installed 12.10 did you tick the box to install third party software?

If this was not done during installation then the Ubuntu Software Centre should be used to install Ubuntu Restricted Extras.

After opening Software Sources and ticking the box labelled Proprietary Drivers for devices (restricted), then open the Additional Drivers tab and select a driver to use. Click apply.

Regards.

---

### Post by Xgen on 2012-10-19
So far, the 12.9 AMD propriety driver works fine for me in precise but not in quantal. The open source one leaves a lot to be desired. I will wait until AMD 12.10 comes out supposedly with support for the latest xserver in quantal.

---

### Post by mwolfe on 2012-10-19
What video card are you running? You need a 5000 series or newer to use fglrx with Ubuntu 12.10 because of some new dependancies on xorg or something like that. Otherwise you'll have to stick with the gallium drivers that came with the system. For me that wasn't an option though because compiz would become incredibly slow after a short time using it.


I have a 5770 card and was able to get the fglrx drivers installed by simply doing 

```
sudo apt-get install linux-headers-generic fglrx-updates
```

You shouldn't need to download the drivers from AMD at all. 

You might want to just try installing linux-headers-generic first and if that doesn't work, uninstall of the the fglrx packages and reinstall fglrx-updates.

---

### Post by Justsum1 on 2012-10-20
> **grahammechanical said:**
> When you installed 12.10 did you tick the box to install third party software?

If this was not done during installation then the Ubuntu Software Centre should be used to install Ubuntu Restricted Extras.

After opening Software Sources and ticking the box labelled Proprietary Drivers for devices (restricted), then open the Additional Drivers tab and select a driver to use. Click apply.

Regards.

I installed ubuntu restricted extras, and still the same thing going on. If i try to install the drivers from  software sources, the install just freezes and stays on the same progress level forever. 

The reason i want the drivers so bad, is that my 5770 is way too loud without them. The drivers adjust the fans on the correct level, and without them my computer sounds like a vacuum cleaner.

Ya i have quantal. Never had any problems with 12.04.

---

### Post by puntigamer on 2012-10-21
Hi,

I have an ATI HD4500. Is there any way to install the ATI/AMD driver on Ubunu 12.10? On 12.04 everything was fine, but now I can't game and my VGA gets sometimes loud :( I could use the AMD driver 12.8 in Ubuntu 12.04 too, may I give 12.9 beta a try in Ubuntu 12.10? Can I cause damage to my VGA or the worst that could happen is breaking Compiz?
Thanks!

---

### Post by northwestern on 2012-10-21
Look at the UbuntuVibes website, followed there instructions for installing AMD,  installed catalyst onto my laptop. Works like a charm.

Regard
Northwestern

---

### Post by puntigamer on 2012-10-22
Thanks, this really works! I've found it on the packagers site: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx) 
This will downgrade X and patch the kernel module to the kernel version 3.5 ;)

---

### Post by garginis on 2012-10-22
Do this 
[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html")

It works, you need to downgrade x.org and install legacy drivers.

I did this, driver works like a charm.I've got only one problem.I can't get GPU Temp.Before installing this driver, i could see GPU temp via sensors or via hwmon.But after install i can't see it.I tried to do sudo sensors-detect but it doesn't read my gpu temp.Does anybody know how to get gpu temp back?

Cheers, Dragan

---

### Post by futu on 2012-11-07
[FONT=Arial]According to what you wrote, you are trying to install amd-driver-installer-12.6-legacy-x86.x86_64.run to Linux 3.5.0-17-generic or any other patch of Linux kernel 3.5.0.

Linux Kernel 3.5 change the way of memory management. Therefore, the old do_mmap is no longer valid but replaced by vm_mmap. You should find an error pointing to do_mmap in /usr/share/ati/fglrx-install.log.

To solve this, you may try the following, that worked for me:

1. Start the installation as usual and wait until the installation GUI comes up[/FONT]
[FONT=Courier New]sudo sh ./[/FONT]amd-driver-installer-12.6-legacy-x86.x86_64.run

2. Startup another Terminal session and locate the temporary installation directory (called something like "fglrx-install.*").

3. Replace ./install/lib/modules/fglrx/build_mod/firegl_public.c from within the temporary installation folder by the file attached to my message

4. Continue with the installation.

Greez, Futu


> **garginis said:**
> Do this 
[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

It works, you need to downgrade x.org and install legacy drivers.

I did this, driver works like a charm.I've got only one problem.I can't get GPU Temp.Before installing this driver, i could see GPU temp via sensors or via hwmon.But after install i can't see it.I tried to do sudo sensors-detect but it doesn't read my gpu temp.Does anybody know how to get gpu temp back?

Cheers, Dragan

---

