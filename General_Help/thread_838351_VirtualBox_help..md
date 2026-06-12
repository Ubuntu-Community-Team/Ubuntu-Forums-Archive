---
title: "VirtualBox help."
date: 2008-06-23
forum: General Help
---

### Post by HpZ on 2008-06-23
I'm on Ubuntu 8.04 and I'm just using VirtualBox becuase I'm interested and it looks cool to be honest. As far as I know this wont effect my OS at all (correct me if I'm wrong). Anyway, onto the problem.

I just did sudo apt-get install virtualbox and ran it. I set it up so that it would run Vista and I put the vista "Service Pack 1" in my disk drive. I selected start and I got this error:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Help?

Also: what is a good memory usage for this if  just want to mess around with it from time to time; nothing serious?

TY,

---

### Post by Het Irv on 2008-06-23
You need to install the "virtualbox-ose-modules-generic" package.  It contains kernal drivers that are needed for VBox to work.  You can use Apt-Get or Synaptic, personal prefrence really.

---

### Post by linux6994 on 2008-06-23
Using the ose version of things will cause troubles if one wishes to us any usb devices on the guest os. Look at these posts and decide which way is best to play for yourself:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

[http://ubuntuforums.org/showthread.php?p=4922723#post4922723](http://ubuntuforums.org/showthread.php?p=4922723#post4922723)

---

### Post by linux6994 on 2008-06-23
The virtual OS world.

There are a several of ways of running alien Operating systems within the host. Whether the* host is Linux (does it better) or Windows the guest OS opens and runs within a window just as another application would. In Linux (Ubuntu) the two most popular are vmware-player and Innotek's Virtualbox. These Linux applications are free, easily installable and each has its benefits. Applications such a Crossover and Parallels are paid applications for both Linux and Windows.

Memory allocation is a definite concern, it becomes a juggling act. If the host on an average desktop has 2gig of memory you might have a virtual OS use 768 or even 1024. You need to allow enough for the host to do what you require it to do. You can on larger systems with available memory have 16 or more virtual machines running on a blade type enviorment depending on the host OS. Linux is a great host OS since virtually you can run any MS either 32 or 64 bit, Sun, any Unix, any Linux and anything else you can think of. Vmware-player (also server) will run more OSs that virtualbox.

Virtualbox allows each virtual machine to be created locally and allows file sharing with the host by having a shared directory. The virtualbox created disks can be set to auto increase in size as the virtual file system expands.

vmware-player uses pre-created machines that are created on sites such as easyvmx.com. The machine parameters are entered and a resulting .zip file is the unzipped to create the directory on the host that contains the virtual disks .vmdk files. The .vmx file contains the machine name, its OS and memory size. The memory size is editable.

---

### Post by badfish591 on 2008-06-23
Well i believe the virtualbox in the repositories does not work with the newest Kernel which is 2.6.24-19, you can check which Kernel you are using by entering the following command (in terminal)
```
uname -r
```
for the newest kernel i beleive you will have to get the version from virtualbox.org and then it should work for you. Also if you are going to run a virtual machine i would really suggest using Xp instead, Vista really takes a bunch of resources. and how much ram you allocate depends on what you have in your machine, i really think 512mb is the minimum, 1gb if you want it to run well. Now if your dead set on using Vista than your going to have to give it more i think.

*EDIT* damn i must type slow, three people beat me

---

### Post by HpZ on 2008-06-23
Still wont work. I get the same error.

---

### Post by HpZ on 2008-06-23
Okay, I have another question. So instead of creating a new thread, I'll ask here.

Can I dual boot with XP without re-installing Ubuntu. As far as I know, the easist way to dual boot with Ubuntu and XP is in the Ubuntu installation wizard. I don't want to lose all my files though. If anyone knows can you offer me a link to a guide?

TY

---

### Post by lizzard on 2008-06-23
Instead using the OSE version from the repositories you can download and install it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")
After a kernel update you are able to recompile the vboxdrv module but just entering:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by linux6994 on 2008-06-23
Folks id does work, I am running virtualbox and vmware player
Look at the prior posting in this thread.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

---

### Post by linux6994 on 2008-06-23
You need to install the following modules see attachment

---

### Post by gfg on 2008-06-23
> **HpZ said:**
> Okay, I have another question. So instead of creating a new thread, I'll ask here.

Can I dual boot with XP without re-installing Ubuntu. As far as I know, the easist way to dual boot with Ubuntu and XP is in the Ubuntu installation wizard. I don't want to lose all my files though. If anyone knows can you offer me a link to a guide?

TY

[This]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm") guide is pretty useful, and should help you dual boot vista or xp, with Ubuntu even if you install them after Ubuntu.

---

### Post by BLTicklemonster on 2008-06-23
Sweet, I've been looking for that information in that concise of a format for a while. Thanks.

---

