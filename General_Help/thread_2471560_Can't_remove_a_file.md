---
title: "Can't remove a file"
date: 2022-02-03
forum: General Help
---

### Post by georgesgiralt on 2022-02-03
Hello Guys,
I've tried to run a vmware machine using vmware player on my Ubuntu 20.04.3 LTS machine just to find it was corrupt. 
So I decided to remove vmware player using it's uninstaller option. 
So far so good...
But as I'm a bit paranoid I did search for leftovers by Mr Vmware...
and found 
```
/sys/module/kvm/parameters/enable_vmware_backdoor
```
which is a one character file... 
So I did this :
```
#ls -ltr /sys/module/kvm/parameters/enable_vmware_backdoor
-rw-r--r-- 1 root root 4096 févr.  3 06:49 /sys/module/kvm/parameters/enable_vmware_backdoor
# rm -f /sys/module/kvm/parameters/enable_vmware_backdoor
rm: impossible de supprimer '/sys/module/kvm/parameters/enable_vmware_backdoor': Opération non permise
# getfacl /sys/module/kvm/parameters/enable_vmware_backdoor
getfacl*: suppression du premier «*/*» des noms de chemins absolus
# file: sys/module/kvm/parameters/enable_vmware_backdoor
# owner: root
# group: root
user::rw-
group::r--
other::r--
#

```
So I wonder what prevents removing of this file ? 
Any help would be greatly appreciated !
Have a nice and bright day !

---

### Post by Impavidus on 2022-02-03
I don't know about vmware. I do know that /sys is a pseudofilesystem. There are no real files in there, but information about the currently running system. Have you rebooted since removing vmware?

---

### Post by georgesgiralt on 2022-02-03
No I did not.
And did not notice the location of the file too. 
One must not try to mend computer *before* having a strong black coffee ...
Should have known that !
Thank you I'll reboot today and see how it goes.

---

### Post by georgesgiralt on 2022-02-04
Hello !
Here I am again. I restarted the laptop this morning.
The file is still here. 
How could I find which module create it ? Because I've searched for modules containing "vm" and only found the Intel's VMD raid controller one ... which is not, IMHO the culprit... 
Thanks a lot for your help !

---

### Post by Holger_Gehrke on 2022-02-04
The virtual filesystem mounted at /sys holds various parameters for the kernel as "files". It's used for reading and writing these parameters. The variable '/sys/module/kvm/parameters/enable_vmware_backdoor' exists on my system, holds a single 'N' (which I interpret as meaning 'not enabled') and I've never had vmware installed. Based on the location and name of this 'file' I'd say it's a parameter for the Kernel-based virtual machine to open up a special access for vmware (or not).

Holger

---

### Post by KBar on 2022-02-04
A minor correction: it's just a parameter (i.e. *enable_vmware_backdoor*) for that loaded module (i.e. *kvm*). You were probably instructed to install dependencies&#8212;perhaps its bundle already includes them&#8212;and to enable a bunch of modules for it to work properly. [KVM]("https://help.ubuntu.com/community/Loadable_Modules") is a loadable kernel module, or LKM for short. They are basically device drivers that aren't compiled into the kernel&#8212;thus they don't take up memory&#8212;and they can be inserted on-demand. When "dormant", they reside in the */lib/modules/`uname -r`/kernel/arch/* as *.ko* files, predominantly.
> [FONT=courier new]The **sysfs** filesystem is a pseudo-filesystem which  provides an interface to kernel data structures. (More precisely, the  files and directories in **sysfs** provide a view of the *kobject* structures defined internally within the kernel.) The files under **sysfs** provide information about devices, kernel modules, filesystems, and other kernel components.[/FONT]
A user may decide to enable certain functionalities that one of these modules provide. To insert a module, say *kvm*, one invokes [FONT=courier new]sudo modprobe kvm[/FONT]. This creates a character special device node */dev/kvm* and also enables the device support until system reboot or its removal. Loaded modules appear in separate subdirectories, named after each one of them, in */sys/module*. In each module's subdirectory, there's a bunch of other directories that mainly provide information, statistics and a way to control them or their behavior. Think of it as a "front-end" to modules. The *parameters* do just that. Some of *kvm*'s parameters are documented [here]("https://docs.kernel.org/virt/kvm/halt-polling.html#module-parameters"). 

Other important subdirectories are *coresize* and *initstate*: the former contains a numerical value denoting the amount of memory used by that module, while the latter holds a text string revealing the state of that module. To access these values, one simply invokes **cat** on them. Some of them are read-only, some of them accessible to root only. 

The *kmod* package provides many useful tools for module management. Run [FONT=courier new]dpkg -L kmod | less[/FONT] to examine the list of files it installed on your system. **lsmod**, for instance, lists all modules currently loaded into the kernel, showing additional information about their memory usage (*coresize*) and other dependent modules (*holders*).

I'm not sure if the KVM module is enabled by default on Ubuntu Desktop installations but I have it, too, for some reason even though I run Oracle VM VirtualBox for testing purposes.

**sysfs**(5), **lsmod**(8)
[https://www.kernel.org/doc/html/latest/filesystems/sysfs.html](https://www.kernel.org/doc/html/latest/filesystems/sysfs.html)

---

### Post by georgesgiralt on 2022-02-04
Hello !
Thank you for your answer. 
kvm modules is loaded on my laptop. Modinfo tell me that  "enable_vmware_backdoor" is a boolean. So this explains the file and it's content. 
As per the loading, no kvm entry in any part of /etc/modules. So I suspect this module is loaded either when you activate virtualization in BIOS or install and activate virtualization software (I've Oracle Virtualbox, and it has a process active at boot).
I leave the file where it sits and let the laptop run it's life...
Thanks a lot for your help !

---

### Post by KBar on 2022-02-04
> **georgesgiralt said:**
> So I suspect this module is loaded either when you activate virtualization in BIOS or install and activate virtualization software (I've Oracle Virtualbox, and it has a process active at boot).
I leave the file where it sits and let the laptop run it's life...

With my extremely limited knowledge in programming, I grepped the source  code of Oracle VM VirtualBox and come across a bunch of files and  functions that seem to indicate that KVM is loaded by VirtualBox. If you're still using it, best leave the modules it loads on and alone.

> Thanks a lot for your help ! 

My pleasure.

---

### Post by georgesgiralt on 2022-02-05
We conclude the same thing. This module is used when virtualization is needed. And I need it with VirtualBox, even if I dumped the VMWare player.

---

