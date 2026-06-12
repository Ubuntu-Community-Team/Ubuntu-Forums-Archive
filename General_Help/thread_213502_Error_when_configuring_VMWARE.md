---
title: "Error when configuring VMWARE"
date: 2006-07-11
forum: General Help
---

### Post by disturbd on 2006-07-11
I had VMWARE installed and running fine the other day. Now today when I tried the icon nothing happened so i tired opening it from terminal. It said i needed to reconfigure the configuration. While doing this i get to this point:

What is the location of the directory of C header files that match your runningkernel? [/usr/src/linux/include]

last time i was able to use the default folder. now when i try, i get this:

The directory of kernel headers (version 2.6.15-25-k7) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.


What do I do?

---

### Post by disturbd on 2006-07-11
Also getting this one:

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]



This makes no sense because it was working just the other day. I have not changed anything that I know of.

---

### Post by givré on 2006-07-11
This is due to the new kernel update. Vmware use module that need to be compile for each kernel. So each time you install or update a new kernel, you need to recompile them. So you need to install linux-headers for the new kernel (2.6.15-26) and reconfigure vmware.

---

### Post by disturbd on 2006-07-11
How/Where do i get those? Im somewhat new to linux.

---

### Post by givré on 2006-07-11
ok, that's quite easy. Open synaptic and search for linux-headers. Install the one that correspond to your running kernel (type 'uname -r' to know it).
When it's done,you just have to reconfigure vmware in a terminal with
```
vmware-config.pl
```
and it should be ok

---

### Post by matrooswolf on 2006-07-11
This should do the trick:
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

more info in this thread:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by disturbd on 2006-07-11
Did both of the above. Now when I try to reconfigure VMware i get this:

> Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/tmp/vmware-config0/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config0/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by disturbd on 2006-07-11
anyone?

---

### Post by mbeierl on 2006-07-11
I do believe

```
sudo -s -H
export CC=/usr/bin/gcc-3.4
perl vmware-config.pl
```

is what you want.  By default, the kernel is build with gcc v3.4, and the standard gcc on ubuntu is v4.0

---

### Post by radiazo on 2006-07-11
A little question: what version of vmware you use? Server, player or workstation. Maybe is possible to configure it with synaptic using the correct section of the repositories.

---

### Post by disturbd on 2006-07-11
i tried that and got the same error. any other ideas? it was working fine until that kernel update this morning but the fix everyone else used isn't working for me. I dunno why. I even tried reinstalling VMware and doing it all again.

---

### Post by disturbd on 2006-07-11
> **radiazo said:**
> A little question: what version of vmware you use? Server, player or workstation. Maybe is possible to configure it with synaptic using the correct section of the repositories.

i am using VMware Server RC 2

---

### Post by radiazo on 2006-07-11
sorry but only vmware player is in the repositories. Are you using vmware for  any special purpose? posibly you replace without hitches vmware-server with vmware player. vmware player are in the multiverse repo.

---

### Post by yetanothersteve on 2006-07-11
I had the same issue after the kernel update from 2.6.15-25 to 2.6.15-26.

I am using vmware-player.

Through Synaptic I marked **Build-Essential** for reinstallation, and I marked **linux-headers-2.6.15-25-386** for complete removal and I marked **linux-headers-2.6.15-26-386** for installation. 

Reran  [INDENT]sudo vmware-config.pl[/INDENT]
and everything worked well.

Yes I know the player is available through one the repositories but I had problems with the kernel module when I installed that way.

---

### Post by radiazo on 2006-07-11
with vmware player you dont need to install manually or compile modules, only install these packages:
vmware-player
vmware-player-kernel-modules
The packages are in the multiverse repo. Be careful! uninstall your current vmware player instalation before of the apt-get or synaptic installation.

---

### Post by disturbd on 2006-07-11
Bah. Now Im getting errors when trying to install VMware Player as well. I tried using Synaptic and apt-get but synaptic halfway installs and gets an error. apt-get installs it but there is no vmware-config file.

How can i completely remove everything left behind. theres folders all over with vmware stuff in them.

---

### Post by radiazo on 2006-07-12
You need to uninstall vmware first. they have a command (I think is vmware-uninstall.pl, but I'm not sure). after you install vmware-player without problems and don't need to use te vmware-config anymore. the access is now trough the menu applications/system tools/vmware player. Please make a backup of your virtual machines before you uninstall anything.
Cheers,

Ronald

---

### Post by disturbd on 2006-07-12
alright. i did that but im still getting that error and when i install its still going through the config and everything. i downloaded it from thr vmware site. should i get it from somewhere else?

EDIT: just tried the one from synaptic again. it gives me an error while configuring through the instal. then when i start it and try to load a Virtual Machine i get a few errors....

---

### Post by radiazo on 2006-07-12
please post the errors in the start of vmware player (after you install it from synaptic) and the instalation errors showed in synaptic

---

### Post by reztho on 2006-07-12
Vmware player uses a kernel module which normally is supplied by the repositories. But right now there is no vmware kernel module for the new kernel update. So actually vmware player is broken until: a) you get the vmware-kernel-module-source from the repositories and compile it yourself, b) the repositories change with a new vmware kernel module compiled for the latest kernel:

 sudo aptitude search vmware
i   vmware-player                                                 - Free virtual machine player from VMware
i A vmware-player-kernel-modules                                  - vmware-player kernel module dependency package
p   vmware-player-kernel-modules-2.6.15-23                        - vmware-player modules for Linux (kernel 2.6.15)
i   vmware-player-kernel-modules-2.6.15-25                        - vmware-player modules for Linux (kernel 2.6.15)
p   vmware-player-kernel-source                                   - Source for the vmware-player-kernel drivers.
i   xserver-xorg-driver-vmware                                    - X.Org X server -- VMware display driver

---

### Post by Pyroxene on 2006-07-13
> **yetanothersteve said:**
> I had the same issue after the kernel update from 2.6.15-25 to 2.6.15-26.

I am using vmware-player.

Through Synaptic I marked **Build-Essential** for reinstallation, and I marked **linux-headers-2.6.15-25-386** for complete removal and I marked **linux-headers-2.6.15-26-386** for installation. 

Reran  [INDENT]sudo vmware-config.pl[/INDENT]
and everything worked well.

Yes I know the player is available through one the repositories but I had problems with the kernel module when I installed that way.

Your solution worked perfectly running VMWare Server.  It answered exactly the questions the system was asking.  I was up an running in 30 minutes.  Many thanks.

---

### Post by andylawrence on 2006-07-13
I may have overlooked it in a earlier post, but if you install linux-headers-386 or linux-headers-686 (whatever kernel version you are running) this is a meta package for the header files and your headers will be updated everytime the kernel is updated.

---

### Post by zygous on 2006-07-17
> **reztho said:**
> Vmware player uses a kernel module which normally is supplied by the repositories. But right now there is no vmware kernel module for the new kernel update. So actually vmware player is broken until: a) you get the vmware-kernel-module-source from the repositories and compile it yourself, b) **the repositories change with a new vmware kernel module compiled for the latest kernel**

Does anyone have an ETA for a new vmware kernel modules package?

---

### Post by thecdn on 2006-07-19
I just installed ubuntu in vmware server running under windows xp. I did all possible upgrades and am now running with kernel 2.6.15-26. 

In synaptic a search for linux-headers lists only variants of linux-headers-2.6.15-23-386, nothing about linux-headers-2.6.15-26-386.

This seems to be preventing me from running vmware tools config. Any idea what I'm missing and why I can't see the linux-headers-2.6.15-26-386 that everyone seems to be referring to?

Btw, the search for linux-headers also lists linux-headers-2.6.15-23, linux-headers-2.6.15-23-386, linux-headers-386, and linux-source-2.6.15 as installed.

---

### Post by givré on 2006-07-19
What is your /etc/apt/source.list?

---

### Post by thecdn on 2006-07-19
> **givré said:**
> What is your /etc/apt/source.list?

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
# Dapper Security Updates
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
# Dapper Bugfix Updates
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
##############################
### Automatix Repositories ###
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
## created by automatixrepo2
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

---

### Post by givré on 2006-07-19
> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
The deb line should not be comment here. I guess it's the problem since the new kernel come in the security channel

---

### Post by givré on 2006-07-19
Where did you get this source.list? Is this an automatic one?
If this is the case, you should contact the guy which done it, since those line are quite important.

---

### Post by thecdn on 2006-07-19
> **givré said:**
> Where did you get this source.list? Is this an automatic one?
If this is the case, you should contact the guy which done it, since those line are quite important.

I used both easyubuntu and automatix with this one. I'm just playing with installing ubuntu on vmware at work to prove to the powers that be that it can be done. 

(Yes, I'm secretly hoping that we get linux on the desktop with windows running on vmware if need be. But that's a long term campaign goal...)

So I didn't pay very close attention to who was doing what with the source.list, but I will pay closer attention next time.

Thanks for the help.

---

### Post by givré on 2006-07-19
> **thecdn said:**
> I used both easyubuntu and automatix with this one. I'm just playing with installing ubuntu on vmware at work to prove to the powers that be that it can be done. 

(Yes, I'm secretly hoping that we get linux on the desktop with windows running on vmware if need be. But that's a long term campaign goal...)

So I didn't pay very close attention to who was doing what with the source.list, but I will pay closer attention next time.

Thanks for the help.

Oh well, good luck 8)

---

