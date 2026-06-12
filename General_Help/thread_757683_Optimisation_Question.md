---
title: "Optimisation Question"
date: 2008-04-17
forum: General Help
---

### Post by martrn on 2008-04-17
I was grepping through the ubuntu reposotory by apt-cache search -ing looing for the words linux and kernel and I found amoungs other things the following :-

> 
linux-image - Generic Linux kernel image.
linux-image-386 - Linux kernel image on 386.
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-ume - Linux kernel image on 386 Embedded/Mobile
linux-image-virtual - Linux kernel image geared towards virtualised hardware
linux-image-rt - Linux kernel image on realtime kernel
linux-image-xen - Linux kernel image on Xen

linux-image-debug-generic - Linux kernel debug image for generic kernel image
linux-image-debug-386 - Linux kernel debug image for 386 kernel image
linux-image-debug-server - Linux kernel debug image for server kernel image
linux-image-debug-ume - Linux kernel debug image for ume kernel image

linux - Generic complete Linux kernel.
linux-386 - Complete Linux kernel on 386.
linux-generic - Complete Generic Linux kernel
linux-server - Complete Linux kernel on Server Equipment.
linux-ume - Complete Linux kernel on 386 Embedded/Mobile
linux-virtual - Complete Linux kernel geared towards virtualised hardware
linux-rt - Complete Linux kernel on realtime kernel
linux-xen - Complete Linux kernel on Xen


linux-image-2.6.22-14-386 - Linux kernel image for version 2.6.22 on i386
linux-image-2.6.22-14-generic - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-server - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-virtual - Linux kernel image for version 2.6.22 on x86
linux-image-debug-2.6.22-14-386 - Linux kernel debug image for version 2.6.22 on i386
linux-image-debug-2.6.22-14-generic - Linux kernel debug image for version 2.6.22 on x86/x86_64
linux-image-debug-2.6.22-14-server - Linux kernel debug image for version 2.6.22 on x86/x86_64
linux-image-debug-2.6.22-14-virtual - Linux kernel debug image for version 2.6.22 on x86
linux-kernel-devel - Linux kernel hacking dependencies
linux-image-2.6.22-14-rt - Linux kernel image for version 2.6.22 on RT kernel
linux-image-2.6.22-14-ume - Linux kernel image for version 2.6.22 on Ubuntu Moblie and Embedded
linux-image-2.6.22-14-xen - Linux kernel image for version 2.6.22 on This kernel can be used for Xen dom0 and domU

Now this leads me to have several questions, regarding kernels on ubuntu.

1.  How can you optimise your ubuntu system and make sure you are using the correct kernel.  Is there a list of kernels you can install for your ubuntu syttem using 'sudo apt-get install linux-generic' or simular and the what is the best 'complete kernel' you can put on to your ubuntu system for example if you have a Pentium 4 or a AMDXP,  so you that you can have or get the correct performance for your system ?

2.  What are linux-xen / linux-rt / linux-ume / linux-virtual complete kernel packages for ?

3.  Preveviously in the ubuntu dapper reposotories (apparently), there were kernel images for K6 processors sperate from kernel images for Intel Pentiums, why are there not seperate images for all the diffrent processesors eg PentiumIII's Pentium IV's, AMD Atholon Xps' Amd Sempron's ect anymore and how do you know which kernel image to install that would be more optimised for you 32 bit system ?

4.  I belive there are patches for the linux kernel at large (correct me if I am wrong), how can you get these patches and patch your own kernel image.

Thanks for any and all responces folks.

---

### Post by kirsis on 2008-04-17
1. The only way you can optimize your kernel is by downloading the source, configuring it and recompiling it yourself. Check google or ubuntu wiki for help on this.

3. Having a lot of different kernels makes bug tracking/fixing a whole lot harder, afaik, so Ubuntu only ships with a generic kernel that's not optimized but that should work on most systems.

4. kernel.org is probably where you ought to be looking

---

### Post by danwood76 on 2008-04-17
2.
these are the kernel image compiled with various add ons.
for example the linux-xen is the xen kernel fro virtualisation (check xen on google)
they are only useful if you want that specific kernel.

btw you cant apply the patches at kernel.org to a kernel image only to the source tree.
They basically do updates between different versions so you dont have to download the entire source again.

---

### Post by martrn on 2008-04-18
Hi,
I have tried to rebuild my kernel just changeing a few switches to try to optimise it a bit for my maching a little following your advice and that from from [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835") I tried to rebuild my kernel. useing that as a rough guide.  I tried :-
```

uname -r
sudo apt-get update
sudo apt-get install build-essential gcc libqt3-mt-dev
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
sudo apt-get upgrade
cd /usr/src
ls
sudo tar --bzip2 -xvf linux-source-2.6.22.tar.bz2
ls
sudo ln -s /usr/src/linux-source-2.6.22 /usr/src/linux
cd /usr/src/linux
sudo make oldconfig
sudo make menuconfig
```
I change a few switches here to optimise it for my machine.  And then I continued :-

```
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-martamdx86athXP kernel_image kernel_headers
```

At this point I went for a cup of hot choclate, and then came back.  And then I went off to read a book and then come back and then I left it becuase it was becomming clear this was going to take some time.

After several hours... I did....
```
cd /usr/src
ls
sudo dpkg -i linux-image-2.6.22.9-martamdx86athXP_2.6.22.9-martamdx86athXP-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.22.9-martamdx86athXP_2.6.22.9-martamdx86athXP-10.00.Custom_i386.deb
sudo reboot
```

When boot up via grub and err the kernel I guess I compiled I can only boot into a terminal with no X11/Xwindows.  I have an nvidia driver the other two ubuntu built kernels one for the server and on generic, and they boot fine into x11/xserver.

How can I test err the kernel I guess I compiled with the nvidia driver.. ??? :confused:

---

### Post by danwood76 on 2008-04-18
For your new kernel version you will need to install the nvidia driver again.
Each kernel version has its own set of mudules which does mean you have to rebuild a few modules after the recompile.
The main thing you have to rebuild is the graphics driver modules to be the same as your original kernel.
Or you can change your xorg.conf to use the vesa driver if you want to get back into X quickly to use some graphical tool to install the drivers.

Note that you probably wont be able to use the restricted drivers manager to install the drivers as your kernel is now a different version (2.6.22.9-martamdx86athXP....)
Just install the drivers the manual way and you should be ok!

---

### Post by martrn on 2008-04-18
> For your new kernel version you will need to install the nvidia driver again. Each kernel version has its own set of mudules which does mean you have to rebuild a few modules after the recompile.
The main thing you have to rebuild is the graphics driver modules to be the same as your original kernel.

OK thanks !  I found and followed the ubuntu's nvidia manual and install that as it said with no apprent problems and it seemed to work fine...
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Or you can change your xorg.conf to use the vesa driver if you want to get back into X quickly to use some graphical tool to install the drivers.

```
// This is what I did :-
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
kdesu kate /etc/default/linux-restricted-modules-common
kdesu kate /etc/X11/xorg.conf
// changed Section/Device/Driver
sudo /etc/init.d/kdm stop
//Then I run the shell script downloaded from nvidia
sudo sh NVIDIA*
// Answer the most likely answers
sudo /etc/init.d/kdm start
```

Note that you probably wont be able to use the restricted drivers manager to install the drivers as your kernel is now a different version (2.6.22.9-martamdx86athXP....)
Just install the drivers the manual way and you should be ok!

OK I installed the nvidia binary drivers, and everything is running sweet.  I can get cool framerates on opengl that I couldn't before, and phonomonely graphics on my nvidia card.  I noticed running GTK/QT apps everything is much more reponsive than it was with the server or generic kernels, It cool, I like.

There is only one prob I can't get to my cds/dvds throgh konqueror, but I'll figure that out later.  Its cool thanks for your advise.

---

### Post by sdennie on 2008-04-18
There may be one last step to manually installing the nvidia drivers for a custom kernel.  If on reboot, if the machine no longer comes up to Xwindows and only re-installing the driver helps, you maybe have to remove several packages.  nvidia-glx-new and nvidia-kernel-common are the likely suspects but, you'd have to google to see if that's correct.  Also note that removing the packages that are causing the problem will mean that you will then have to manually install the nvidia driver you downloaded into the Ubuntu kernels (you can use the -K option on the installer so it only installs the kernel module and not the entire driver package).

Of course, if you reboot and everything comes up fine, just ignore this.

---

