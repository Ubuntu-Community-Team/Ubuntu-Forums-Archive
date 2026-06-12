---
title: "Ubuntu kernel doesnt want to work"
date: 2007-03-08
forum: General Help
---

### Post by juice99 on 2007-03-08
i had problems installing 6.06/6.10 or alpha 5 ubuntu - they were all failing on first step, when waiting bar was being showed without any message. And my hardware is ok, debian works fine, windows works fine. My CD are fine, i checked them. so... I finally managed to install 6.06 ubuntu using this guide [https://help.ubuntu.com/community/In...n/FromUSBStick](https://help.ubuntu.com/community/In...n/FromUSBStick) 

but it has 2.6.15 kernel, and my network card is working only from 2.6.19+ (it is built-in network card)

i have Gigabyte GA-965P-S3 motherboard with 500GB sata2 drive connected to ICH8

so i tried to use 2.6.20 kernel from feisty (upgraded all packages that were needed for linux-image-2.6.20) but the system didnt boot up! failed to mount the root filesystem blah blah blah :/

so i just upgraded with apt-get upgrade and dist-upgrade to 6.10 (with 2.6.17)


So i tried to compile 2.6.20.1 and 2.6.19.7 by myself from the sources, but i get these messages:

[http://cba.pl/sys9/crash/DSC00035.JPG](http://cba.pl/sys9/crash/DSC00035.JPG)

this is my dmesg from working 2.6.17 (ubuntu-made one):
[http://cba.pl/sys9/crash/dmesg](http://cba.pl/sys9/crash/dmesg)

these are two of _MANY_ configs i tried when trying my own kernel:
[http://cba.pl/sys9/crash/conf1](http://cba.pl/sys9/crash/conf1)
[http://cba.pl/sys9/crash/conf2](http://cba.pl/sys9/crash/conf2)

This is my grub menu.lst:
[http://cba.pl/sys9/crash/menu.lst](http://cba.pl/sys9/crash/menu.lst)
Root partition just doesnt want to work what could i forget to compile in ?

I have two options:
- somehow add network card module from 2.6.20 or 2.6.19 to 2.6.17 kernel
- or, make 2.6.19/2.6.20 kernel work on my hard drive/motherboard

i've compiled many kernels before, but this one i can't :( i spent more than 25 hours trying to solve it. lspci is full of Intel - unknown device messages, but that doesnt matter, as this HDD works on 2.6.17 !!! so there MUST be a way! but why it doesnt work on 2.6.20 where my network card works :(

---

### Post by DagMan on 2007-03-08
try downloading a linux image from here [http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-image-2.6.20-8-generic_2.6.20-8.14_i386.deb&md5sum=785a3a5d51c45c13411d09521c68861f&arch=i386&type=main](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-image-2.6.20-8-generic_2.6.20-8.14_i386.deb&md5sum=785a3a5d51c45c13411d09521c68861f&arch=i386&type=main)
and do **not** install it, just right click and open it with the archive manager and extract the config file.  It should be in /boot, in the archive manager, and named config-2.6.20-8-generic

Then dowload the kernel source with ubuntu patches.
[http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-source-2.6.20_2.6.20-9.16_all.deb&md5sum=dbfe47bff05ab9a8b20e0efd181eaddc&arch=all&type=main](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-source-2.6.20_2.6.20-9.16_all.deb&md5sum=dbfe47bff05ab9a8b20e0efd181eaddc&arch=all&type=main)
And install it.  If it won't install, right click on the .deb file like in the above step and extract it using the archive manager, then copy the file linux-source-2.6.20.tar.bz2 to /usr/src

Compile it. Use this guide if you need step by step instructions. [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
It says dapper but will work for Edgy and Fiesty as well.  Make the proper changes by being sure to substitite 2.6.15 with 2.6.20 wherever needed or you'lle end up with the wrong kernel, be sure to apt-get the dependancies shown at the beginning of the guide (except for kernel-source or linux-source) in case your upgrade wasn't perfect and you're lacking something for the build.
Very important, when you get to the step that says sudo cp /boot/config-`uname -r` ./.config
Copy the config file that you got in the first part instead, sudo cp /location/of/file/config-2.6.20-8-generic ./.config

I hope that works for you.  I've compiled that kernel on dapper and edgy like that and it has worked.

Good luck.  I'm curious how it goes.

---

### Post by juice99 on 2007-03-08
ubuntu doesnt support my graphics card, and i see people complaining about it all over the place, so i didnt even mention it. It is Ati 1950 pro , but it doesnt matter, as first i'm trying to at least run this in text mode. but i think i will manage to unpack it under console and do everything what you said..

i just don't know if i will have enough energy to actually use this OS , after i finish trying all this. i spent 30+ hours already on this problem. and so many people got the same issue: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

---

### Post by tagginannie on 2007-03-09
> **juice99 said:**
> ubuntu doesnt support my graphics card, and i see people complaining about it all over the place, so i didnt even mention it. It is Ati 1950 pro , but it doesnt matter, as first i'm trying to at least run this in text mode. but i think i will manage to unpack it under console and do everything what you said..

i just don't know if i will have enough energy to actually use this OS , after i finish trying all this. i spent 30+ hours already on this problem. and so many people got the same issue: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

Got something you try if you want but you need to know access
mode, capacity, number of cylinders, number of heads, write
precomp, landing zone, and number of sectors for each drive 
because you need to enter that information. OK, reboot and press
"F1"  to get in to your bios setup turn off the IDE/SATA auto
detection and enter the drive(s) information Press "F10" to save and
reboot to see if you can boot with new kernel. If not go back to
using an older one. 

And as for your video card you can download drivers for it from ATI/AMD[U]
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("ttp://ati.amd.com/support/drivers/linux64/linux64-radeon.html")[/U]

---

### Post by juice99 on 2007-03-09
ok it started working! i don't know how and why. i didnt do what you describe here other than switching off IDE/SATA controller. but the strangest thing is that when i turn it on, sometimes it even works then!

it's like 50/50 chance to get system started everytime. someone mentioned race condition happening - yes, that would be explaining all the troubles.

i don't know why sudennly it works even with SATA/IDE turned on. this is strange issue and probably hard to analyze, as some people saying that it doesnt exists anymore and some that it does.

but i'm pretty sure it DOES exists, even if in my case it started working. i'm not touching ubuntu installator anytime soon, until this got fixed, and fixed for good. thanks for help all.

to others trying to figure out what to do:

- stay with dapper for now, if you can, if not
- install dapper from alternate or from USB, then update to feisty but with full dist-upgrade, then turn off SATA/IDE controller in BIOS

it worked for me

---

