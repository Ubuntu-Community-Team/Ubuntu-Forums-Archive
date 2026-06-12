---
title: "Completely uninstalling virtualbox"
date: 2008-03-10
forum: General Help
---

### Post by WebDrake on 2008-03-10
Hello all,

A week or so ago I tried installing Virtualbox on my Kubuntu Gutsy system as per the instructions here:
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I decided I didn't like or particularly need it and so uninstalled it (sudo aptitude remove virtualbox-ose) but this has not removed the virtualbox kernel module---or rather, I suspect the system still *looks* for the module but can't find it.

I'm noticing messages in the syslog along the following lines:
```

kernel: [ 1657.192000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
kernel: [ 1657.192000] vboxdrv: Successfully done.

```

... and a message during the shutdown process: "modprobe vboxdrv failed".

How do I completely remove vboxdrv from my system?  I tried "sudo rmmod vboxdrv" but got back an error message, "ERROR: Module vboxdrv does not exist in /proc/modules".

Thanks in advance,

    -- Joe

---

### Post by luisromangz on 2008-03-10
Maybe the virtualbox-ose-modules-<kernel version> package is still installed.

---

### Post by WebDrake on 2008-03-10
Nope, it was uninstalled.

When installing VirtualBox it's not sufficient to install the packages, you have to do a little extra to install the vbox kernel module:
```

sudo apt-get install virtualbox-ose virtualbox-ose-source
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant unpack virtualbox-ose
sudo module-assistant auto-install virtualbox-ose

```
(from the instructions at [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) )

I think it's the latter commands that have left over something (or more likely, the expectation of something) on the part of the kernel.

modprobe -l vboxdrv gives the output "/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko" but that file/directory no longer exists.  So this must be the source of the error message.

---

### Post by zhanglini on 2008-06-06
A related question---how do I get my harddrive space back?  
I deleted the virtual harddrive before I uninstalled virtualbox, but I still have some space missing.
Thanks

---

### Post by mrpeenut24 on 2008-06-06
PLEASE SOMEBODY HELP ME!!

I had a similar problem.  I downloaded the .deb file from their website and installed it.  I also decided I didn't like it so I ```
sudo apt-get remove VirtualBox
``` it.  It kept telling me that it couldn't load the vboxdrv module, but I assumed that when I updated, a new minor kernel would realize it wasn't there and fix it.  So today the 2.6.24-18 installed and I got this message:
> 
/etc/init.d/dkms_autoinstaller: line 82: /var/lib/dkms/vboxdrv/1.6.0/source/dkms.conf: No such file or directory
vboxdrv (1.6.0): AUTOINSTALL not set in its dkms.conf.

I didn't think much of it, just that it was trying to compile it back into the kernel again.  No big deal, it just won't load.  WRONG!  Now whenever I try to boot, it gives me > Error 15: File not found  I tried to boot with the older kernel, and it gives me the same error.  I've reinstalled grub, but no success.  I'm not sure how it could have messed up the older kernel, but I don't know how to recompile it if I can't boot into it.

Someone PLEASE help me!  As of now, my laptop is a paperweight.




> **zhanglini said:**
> A related question---how do I get my harddrive space back?  
I deleted the virtual harddrive before I uninstalled virtualbox, but I still have some space missing.
Thanks

delete the folder ~/.VirtualBox or around thereabouts.  There will be a .vdi file and some others.  This is the partition that you created.  Delete the entire directory to get your space back.

---

### Post by zhanglini on 2008-06-06
> 
delete the folder ~/.VirtualBox or around thereabouts.  There will be a .vdi file and some others.  This is the partition that you created.  Delete the entire directory to get your space back.

Thanks, I did the following and it works:
```
 sudo rm /home/yourname/.VirtualBox/VDI/XP.vdi 
```

---

### Post by mrpeenut24 on 2008-06-06
Glad to hear it.  Also, I found out what was wrong with mine; the menu.lst had been changed by the upgrade to show that all of my images were on a different partition... *shrug*.  So I fixed that part.  But I *still* have the error message about the vboxdrv not being found.  Anyone know how to get rid of it?

EDIT:  Nevermind, I found how to do that too.  Removing the /var/lib/dkms/vboxdrv directory, then recompiling the kernel images did the trick. :-D

---

