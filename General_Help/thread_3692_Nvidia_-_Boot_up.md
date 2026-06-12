---
title: "Nvidia - Boot up"
date: 2004-11-08
forum: General Help
---

### Post by spirospr on 2004-11-08
I am a newbie in linux. I just installed UBUNTU 4.10 on my Dell latitude D800. I 'm facing two problems.

1. During boot up  i get the following message

modprode : Fatal : Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

Which i have no idea what is about . Some hardware recognition i guess......

2. I try to install  nvidia drivers following instructions from nvidia site. I 'm doing the following steps :

I startup through failsafe mode and as root i run the nvidia installer

sh NVIDIA-Linux-x86-1.0-6106-pkg1.run

the istallation begins  and i get the following messages :

WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com](ftp://download.nvidia.com))? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed. If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

so as a newbie i have no idea how to fix things , any help would be nice . 


Dell latitude D800 , Nvidia Cefore4 4200Go , Wireless Broadcom 802.11b , Bluetooth , Broadcom Ethernet , Ac97 Audio controller , Intel pentium M 1,6 MH , WSXGA 15.4" etc. 

Ofcourse most the above are not working but i think that i will solve the problems one by one. 

Thank you.

---

### Post by Rancoras on 2004-11-08
Try this:

[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by spirospr on 2004-11-08
1. How do i know if i have the linux-restricted modules >= 2.6.8.1.1-3 ?

2. Do i have to download the nvidia-glx in order to proceed?


Thak's for your patience, everything seems like chinese for me right now

---

### Post by dawynn on 2004-11-08
I was running Debian Testing using the Nvidia drivers provided specifically by Nvidia (because the Debian packages for NVidia were usually about 5 kernels out-of-date).  I then switched up to Ubuntu Warty and, since that time, to Ubuntu Hoary.  The Restricted modules and Nvidia modules pre-packaged by Ubuntu have worked just fine for me.

That being said, my Nvidia card is not exactly top-of-the-line.  Your mileage may vary.

Go into Synaptic (it's in your System Configuration pull-down menu, or something like that -- I don't use Gnome, sorry) and do a 'Search' for 'linux-restricted-modules.  If Synaptic indicates that none of the linux-restricted-modules packages are installed -- then nothing's installed.

If you don't have any of them installed, it helps much to know a little bit about your system.  Ubuntu allows three kernel options, for us IBM-compatible folk.  Do a search for 'linux-' in Synaptic.  You should (!) have one of three possible kernel meta-packages installed.  Either linux-k7 (use only for AMD machines, Athlon or higher), linux-686 (use only on Pentium 2 or higher), or linux-386 (for all other IBM-compatible machines).  Whichever one you have installed, install the comparable linux-restricted-modules meta-package (so, if you, like me, have an AMD Athlon machine, make sure you have both the linux-k7 and linux-restricted-modules-k7 meta-packages installed).  If you ensure that you have the correct meta-packages installed, then you should always have the correct latest kernel and Nvidia modules installed (assuming you upgrade your system on a regular basis).

Yes, you will want to nvidia-glx, and nvidia-settings packages installed.  Not sure what exactly the nvidia-glx package does, but it updates your XFree Configuration file.  The nvidia-settings package gives you a nice little frontend for tweaking the card, much like the panel tool that the nvidia software installs in Windows.

---

### Post by spirospr on 2004-11-08
Is there a specific folder that i will have to put the nvidia-glx in order to make the installation?

---

### Post by Rancoras on 2004-11-08
When you run the command

```
sudo apt-get install nvidia-glx
``` 

Apt will download the package for you.

---

### Post by spirospr on 2004-11-08
I have no internet connection for the laptop , as almost nothing works right on the laptop now , so i can't see how it will download the package for me...... is there an alternate???

---

### Post by Rancoras on 2004-11-08
Ah, well, then just download the package and use the dpkg command to install it.  It doesn't matter what folder you put the file in.  I guess it would be easiest to put it you home folder.

```
sudo dpkg -i packagename
```

---

### Post by spirospr on 2004-11-10
what should i download for this and from where?

I tryed do this with a debian package that i found named :

nvidia-glx_1.0.6629-1_i386.deb

but i got the reply that package nvidia-kernel-1.0.6629 is not installed

Thank you for your support so far.......

---

### Post by spirospr on 2004-11-10
well it seems like i made it to install the nvidia drivers for my Gforce4200 GO

I downloaded the packages of nvidia-glx from here 

[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.8.1/](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.8.1/)

i transfered it from my other computer to my laptop's directory and gave the command
sudo dpkg -i nvidia-glx-dev_1.0.6111-1ubuntu7_i386.deb

then i followed the instructions from the wiki page

[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

and everything worked smoothly

Thank you all for your help..... :D

---

