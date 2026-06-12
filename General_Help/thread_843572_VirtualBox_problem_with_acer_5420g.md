---
title: "VirtualBox problem with acer 5420g"
date: 2008-06-28
forum: General Help
---

### Post by Dalstal on 2008-06-28
I'm having difficulties making virtualbox work with my new computer,it is an amd 64 processor but I installed the regular version of ubuntu 7.10 on it. Now I can't get virtualbox to start a virtual machine, I only get the message:"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)."
What should I do?
/Mattias

---

### Post by AlesUbu123 on 2008-07-01
Do you have package virtualbox-ose-modules installed?

Try running 
```
sudo /etc/init.d/vboxdrv start
```

---

### Post by Dalstal on 2008-07-04
dalis@dalis-laptop:~$ sudo /etc/init.d/vboxdrv start
[sudo] password for dalis:
 * Starting VirtualBox kernel module vboxdrv                                                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
dalis@dalis-laptop:~$

I think I have the virtualbox-ose-modules installed, how do I check that I have?

---

### Post by AlesUbu123 on 2008-07-05
You could try directly installing, and apt will tell if its already installed anyway:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```
(but be carefull to change 2.6.24-19 to the kernel version of your presently installed kernel!)

It would probably be easier to just go to [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") and download the **binaries** version. This has proved to be much easier for me!

---

### Post by Jose Catre-Vandis on 2008-07-05
Looks like the virtualbox driver has not yet been set up. If you run
```
sudo /etc/init.d/vboxdrv setup
```
it will either work, or (sometimes) tell you what is wrong

---

### Post by Dalstal on 2008-07-05
dalis@dalis-laptop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for dalis:
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
dalis@dalis-laptop:~$

---

### Post by Jose Catre-Vandis on 2008-07-05
Have you also made your user a member of vboxusers group? And use synaptic to find the VirtualBox kernel modules for your distro (host) installation.

If all else fails, go to [www.virtualbox.org](www.virtualbox.org) and download the latest non-OSE version

---

