---
title: "VMware: Unable to change virtual machine power state"
date: 2007-08-15
forum: General Help
---

### Post by niteshadw on 2007-08-15
I get an error when trying to power up a virtual machine:

Unable to change virtual machine power state:The process exited with an error: End of error message.

The system is Ubuntu 7.04. I've used the canonical.com feisty-commercial repositories and all worked until trying to power a virtual machine of windows xp pro.

I've found that it maybe due to the vmmon module, but I have not installed VMware from source so when trying to execute:
modprobe -f vmmon

It says the module is not found. Not sure if this is the right direction but does anyone have any suggestions?

---

### Post by teslaw on 2008-01-07
I guess VMware server modules are not always upgraded (re-compiled) when you upgrade your kernel version. Try to reinstall VMware from repositories or run vmware-config-network.pl 
or recompile modules using module-assistant:
```
m-a build vmware-server-kernel
```
and install created package if you used vmware-any-any-update*.tar.gz files.

---

### Post by p|_eX on 2008-01-09
go to Virtual Machine Settings > Advanced and turn on "Run with debugging information"
it will probably give some more information. 

It could be something with owner / user rights . be sure to check the files (and folder) have the correct owner (usually root).

---

### Post by ndube on 2008-01-17
I had to chown the /home/username/.vmware directory so that my user name and group were the owners.

---

### Post by thirddeep on 2008-04-22
Thanks to p|_eX I found I had the same problem as ndube.

For reference, I used the tar balls from VMware.

Thd.

---

### Post by herda05 on 2008-06-23
I ran into this problem after my kernel was updated (through synaptic).

I did two complete removals through synaptic but still received this error each time I installed and tried to run a vm.

Finally I followed the install steps on [Ubuntu Tutorials]("http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/") and then I ran into a problem compiling the VM perl.

I resolved that through the steps at the bottom of this thread which said to [install lbssl]("http://www.linuxquestions.org/questions/linux-software-2/vmware-server-install-error-the-vmware-vmperl-scripting-api-was-not-installed.-476129/").

Now everything is running fine.

---

### Post by microview on 2008-06-25
If you copied over the vmware image of xp-pro (or any other OS) then be sure to set the owner and permissions in /var/lib/vmware/Virtual Machines/<image name>/*

do a chown <user>:<user> and chmod 755 * on all the files in that directory.

---

### Post by gauss on 2008-07-03
> **p|_eX said:**
> go to Virtual Machine Settings > Advanced and turn on "Run with debugging information"
it will probably give some more information.

Thanks. I had the same problem and debugging revealed that I had a ~/.vmware *file* that I used to store the password, URL, etc. and that vmware-server needed a *directory* with that name. I created one and all is well.

---

### Post by dthompso on 2008-07-15
Kernel upgrade broke my VMWare. This is a PITA, is there any easy way to roll back the kernel version so I don't have to muck around with re-installing VMWare server?

---

### Post by shizakapayou on 2008-07-15
When you're booting up grub should give you the option of picking the kernel to boot.  To fix VMWare, run vmware_install.pl again - it should remember all your prior settings, so you'll mostly just be answering 'yes' to everything.  For more info, check here: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Personally, my experience has been that kernel updates don't happen often enough to be a problem for me.

---

