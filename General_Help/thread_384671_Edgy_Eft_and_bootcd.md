---
title: "Edgy Eft and bootcd"
date: 2007-03-14
forum: General Help
---

### Post by pointone on 2007-03-14
I'm having problems making a boot CD with the bootcd package.

bootcdwrite works flawlessly (as in no errors), I run cdrecord to burn the image (again, no errors), but during boot, the system freezes right after attempting to mount root:

/init: /init: 125: Syntax error: 0xto
Kernel panic - not syncing: Attempted to kill init!

I was originally trying this with a customized system which I wanted loaded onto the CD, but just to troubleshoot, I tried making a boot CD from a fresh install. Same result.

(By fresh install, I mean I installed a basic command-line system from the alternate install disc, only installed the bootcd and cdrecord packages (and their dependencies), and then immediately made the image.)

It's not likely to be the image: I went through the bootcdwrite / cdrecord process three times. I doubt it's a hardware issue, as I tried booting from the CD on three systems.

I know my process is correct because I successfully made a Debian-based boot CD with bootcd / cdrecord not long ago (Debian Sarge 3.1 r4).

Has anyone experienced this before, or know what's going on here? Has anyone successfully made a boot CD with bootcd and Ubuntu Edgy Eft?

Thanks in advance!

---

### Post by Rotaj on 2007-03-14
I am fairly new to this and I may be misunderstanding the question. But, if you have the bandwidth, download the appropiate ISO file and burn it to a CD. That will create a bootable CD.

---

### Post by pointone on 2007-03-15
The bootcd package essentially transfers your current system onto a bootable CD. I have customized my current system to run as an Internet kiosk; I wish to transfer it to a CD to load to multiple computers. However, any attempt to boot from CDs created results in the error described above.

---

### Post by pointone on 2007-03-15
Well, I managed to work around the kernel panic issue by installing and using the bootcd-mkinitrd package, which recreates your initrd to detect the appropriate CD-ROM drive. However, I've now stumbled upon another problem.

The system now freezes right near the end of the boot process. The last few lines displayed are:

lo: Disabled Privacy Extensions
IPv6: over IPv4 tunneling driver
lp0: using parport0 (interrupt driven)

I'm completely stuck again, and really have no idea where to go from here.

I tried disabling the system's swap, since that's (I think) what comes next when the boot succeeds from the installed system, but that made no difference.

Aside from providing a solution, has ANYONE been able to get bootcd to work with Ubuntu 6.10 Edgy Eft? Would anyone care to try a simple test? It's quite simple, really.

Install a command-line system
Enable the 'universe' sources
sudo apt-get install bootcd bootcd-mkinitrd cdrecord
sudo bootcdmkinitrd
sudo bootcdwrite
sudo cdrecord --dev=*,*,* /var/spool/bootcd/cdimage.iso --driveropts=burnfree (replace the *'s with the address obtained by running 'sudo cdrecord --scanbus')
... And try booting with the CD generated

Please help!

---

### Post by lilnerd on 2007-03-16
> **pointone said:**
> Well, I managed to work around the kernel panic issue by installing and using the bootcd-mkinitrd package, which recreates your initrd to detect the appropriate CD-ROM drive. However, I've now stumbled upon another problem.

The system now freezes right near the end of the boot process. The last few lines displayed are:

lo: Disabled Privacy Extensions
IPv6: over IPv4 tunneling driver
lp0: using parport0 (interrupt driven)

I'm completely stuck again, and really have no idea where to go from here.

I tried disabling the system's swap, since that's (I think) what comes next when the boot succeeds from the installed system, but that made no difference.

Aside from providing a solution, has ANYONE been able to get bootcd to work with Ubuntu 6.10 Edgy Eft? Would anyone care to try a simple test? It's quite simple, really.

Install a command-line system
Enable the 'universe' sources
sudo apt-get install bootcd bootcd-mkinitrd cdrecord
sudo bootcdmkinitrd
sudo bootcdwrite
sudo cdrecord --dev=*,*,* /var/spool/bootcd/cdimage.iso --driveropts=burnfree (replace the *'s with the address obtained by running 'sudo cdrecord --scanbus')
... And try booting with the CD generated

Please help!

I think I may be able to help. ARe you trying to use the live CD? And u get to the menu, but the loading bar freezes below where it says ubuntu? That happened to me because I had a ATI x300, so it could be because of an ATI graphics card. IF this is the case then download and install the alternative CD. (It's not that hard to use, just like installing windows) Then if you have a ATI you may get a message that says...Something about X failed to load. So then u click ok...and type in sudo nano /etc/X11/xorg.conf (Remember, Linux is case sensitive) then Find the line driver "ati" change it to "vesa" and then press Ctrl+x, then "Enter" to overwrite. Once ur done that and can get into Ubuntu then tell me. The graphics will suck at this point. So tell me when you're done this and i know how to fix the graphics problem...Hope it helps:popcorn:

---

### Post by pointone on 2007-03-16
Thanks for the reply, but you're still not understanding the issue here.

The bootcd package creates a CD containing the system you currently have installed. You install your system, set it up the way you want, then run bootcdwrite to create an ISO image of your system. I am building a customized system which I want to use on multiple computers. The system is already built; there were no problems at all with this part of the process. Problems appear when using the bootcd software.

Now, I've managed to narrow down the problem further. I believe the issue lies with Edgy Eft's new init system, upstart. For whatever reason, the image created by bootcd is not running all the init scripts on startup; specifically, bootcd is not running the runlevel scripts (i.e., the scripts in /etc/rcS.d/). 

Does anyone have any ideas? Would it be possible to force the bootcd software to recognize these scripts?

---

### Post by Rotaj on 2007-03-16
I think I finally understand what info you are seeeking.  Are these multiple systems of the same configuration?

---

### Post by lilnerd on 2007-03-17
> **pointone said:**
> Thanks for the reply, but you're still not understanding the issue here.

The bootcd package creates a CD containing the system you currently have installed. You install your system, set it up the way you want, then run bootcdwrite to create an ISO image of your system. I am building a customized system which I want to use on multiple computers. The system is already built; there were no problems at all with this part of the process. Problems appear when using the bootcd software.

Now, I've managed to narrow down the problem further. I believe the issue lies with Edgy Eft's new init system, upstart. For whatever reason, the image created by bootcd is not running all the init scripts on startup; specifically, bootcd is not running the runlevel scripts (i.e., the scripts in /etc/rcS.d/). 

Does anyone have any ideas? Would it be possible to force the bootcd software to recognize these scripts?

Sorry i still don't get it... Hope you figure it out

---

