---
title: "How do I run Windows 98 FE in VirtualBox OSE or Qemu?"
date: 2008-03-24
forum: General Help
---

### Post by hurtstotalktoyou on 2008-03-24
Hi, all.

I can't seem to get Windows 98 First Edition installed in a virtual machine.  I've tried both VirtualBox OSE and Qemu, but nothing seems to work.

Here's my stats:
Ubuntu 7.10 Gutsy Gibbon 32-bit edition
Athlon XP 1800+ @ 1.84GHz
768MB DDR SDRAM
nVidia FX5200 128MB

Are there any step-by-step instructions to help me along, here?  Or maybe a list of common problems and solutions?

Any suggestions would be much appreciated.  Thanks!

---

### Post by pytheas22 on 2008-03-24
Where are you having trouble?  I've never installed 98 in VirtualBox, but I have installed Windows XP in it plenty of times on different machines and it's never given me a problem.  Are you able to start the virtual machine and boot to your Win 98 CD?

---

### Post by hurtstotalktoyou on 2008-03-24
Okay, here's what I do:

01.  I go to Synaptic Package Manager and mark "virtualbox-ose" to install.  SPM tells me I need to mark three other packages, too.  They are:  libxalan110, libxerces27, virtualbox-ose-modules-2.6.22-14-generic.  I allow SPM to mark these and install all four packages.

02.  I set up a new virtual machine in VirtualBox OSE.  I set the "OS Type" to "Windows 98", base memory size to 64MB,   I create a 2.00 GB "dynamically expanding image" for my virtual hard disk.

03.  I mount my host floppy drive (/dev/fd0) as my virtual floppy, and my host CD/DVD drive (/dev/cdrom) as my virtual CD/DVD.  I insert boot floppy and Windows CD.

04.  I attempt to start the virtual machine, and get this error:

[indent]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/indent]

Any ideas?

---

### Post by pytheas22 on 2008-03-24
First, make sure you've rebooted your computer after installing VirtualBox (actually, all you really have to do is make sure the relevant modules are inserted, but rebooting is a simpler solution).  If it still doesn't work, it's probably because of permissions: you need to add yourself to the vbox users group.  You can do this using the "Users and Groups" utility available at System>Administration--open the vbox users group, and make sure that the user account you are using to run VirtualBox is a member of that group.

Alternatively, you could just run VirtualBox as root (type "sudo Virtualbox" in a terminal) and it should work, but for various reasons it would be better to do the proper thing and add your user account to the vbox group.  Either way, once the permissions are right, everything should work normally.  Let us know if this works.

---

### Post by hurtstotalktoyou on 2008-03-24
Hmm.  I tried the sudo Virtualbox idea, and got this error (inside Terminal):
[indent]WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-modules package for your kernel.

         You will not be able to start VMs until this problem is fixed.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
[/indent]

This is strange, because I already installed virtualbox-ose-modules-2.6.22 6.  I opened Synaptic Package Manager just to make sure it verifies that the modules package is installed, and sure enough it tells me it is.

Also, when I go to Users and Groups I don't see any options for a VirtualBox group.

Thanks for the help so far!  Let's cross our fingers that we can get this thing in the bag.

---

### Post by pytheas22 on 2008-03-24
Did you try restarting your computer?  And are you sure that you're running on the same kernel as the one for which the VirtualBox .deb package was built?

Also, what is the output of

```
ls /dev | grep vbox
```

and

```
lsmod | grep vbox
```

---

### Post by hurtstotalktoyou on 2008-03-24
Okay, I rebooted and used gksudo virtualbox in Terminal, and things started to work.  I'll post back if I get stuck again.

Thanks, guys!

---

