---
title: "Is it possible to symlink linux-restricted-modules??"
date: 2007-05-07
forum: General Help
---

### Post by kilou on 2007-05-07
Hi,

I'm using Feisty and recently I recompiled the Ubuntu kernel because I had to change the kernel settings and apply a few patches for my config. To do this I installed linux-source-2.6.20 with Synaptics and then reconfigured/compiled the kernel from there. 

Now my new kernel is named 2.6.20.3-ubuntu1-custom while the original one was named 2.6.20-15-generic but the the base is the same since I build the custom kernel with the source of the original one. However now the restricted driver manager doesn't work anymore and aks me to install "linux-restricted-modules-2.6.20.3-ubuntu1-custom"....that obviously doesn't exist of course! 

But since the restricted module of the original kernel is installed I suppose it should be possible to use it with the custom kernel by creating a symlink "linux-restricted-modules-2.6.20.3-ubuntu1-custom" pointing to the installed "linux-restricted-modules-2.6.20-15-generic". However I can't find a folder related to restricted module anywhere...

Is there a way to tell Feisty Fawn to use restricted modules from the original kernel with my custom-compiled Ubuntu kernel???

Thanks

---

### Post by DagMan on 2007-05-07
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper) that older guide explains how to compile restricted modules into a kernel during a kernel compile however I didn't get much out of it with Feisty other than the kqemu module.  I think maybe just apt-get build-dep of the restricted modules, building them, and then doing the same with the package that handles the restricted modules as well.

In my case I need the ipw3945 wireless package... or part of it in restricted modules, the module itself actually builds so it's a deceptive name.  I was able to just rename the firmware folder and an executable and symlinking would have worked in my case but it really is sort of risky to do something like that with hardware and if it was graphics for example there's no way I would have attempted to run it like that.

In direct answer to the question of the Restricted Driver Manager package, it looks to me that it would have to be rebuilt for the kernel.

---

### Post by kilou on 2007-05-07
DagMan, thanks for the link and the information. I probably don't really need restricted drivers because all my hardware (except SD card reader) is working. But it would be nice to have the restricted drivers manager working in case I add something that need proprietary drivers. After compiling the new custom kernel my Wifi card wasn't working as well and I did the same as you: symlinking the /lib/firmware/newkernel to /lib/firmware/oldkernel and it worked after that.

The problem is not with the restricted drivers manager "package" itself, it is that this package looks for the linux-restricted-modules for the active kernel and since it has a fancy name it doesn't find it. After looking a little further I found some folders and files related to restricted modules so I tried to symlink all this to the new kernel name. Here is a list of the symlinks I did so far:

cd /lib/firmware
ln -s 2.6.20-15-generic 2.6.20.3-ubuntu1-custom

cd /lib/linux-restricted-modules
ln -s 2.6.20-15-generic 2.6.20.3-ubuntu1-custom

cd /usr/share/linux-restricted-modules
ln -s 2.6.20-15-generic 2.6.20.3-ubuntu1-custom

cd /var/lib/dpkg/info
ln -s linux-restricted-modules-2.6.20-15-generic.md5sums linux-restricted-modules-2.6.20.3-ubuntu1-custom.md5sums
ln -s linux-restricted-modules-2.6.20-15-generic.postinst linux-restricted-modules-2.6.20.3-ubuntu1-custom.postinst
ln -s linux-restricted-modules-2.6.20-15-generic.postrm linux-restricted-modules-2.6.20.3-ubuntu1-custom.postrm
ln -s linux-restricted-modules-2.6.20-15-generic.list linux-restricted-modules-2.6.20.3-ubuntu1-custom.list

However the restricted drivers manager still ask for linux-restricted-modules-2.6.20.3-ubuntu1-custom to be installed!!!

I'm unsure if the restricted drivers should be compiled in the kernel because in the original configuration they are not. The restricted modules are in another package, separate from the kernel source files so I guess that the symlink method should work if I can find all the files that need to be symlinked.....

Any other symlink I should try to make the restricted drivers manager work with my custom Ubuntu kernel??

---

### Post by rjwboys on 2007-05-08
im haveing a similar problem and hadn't got much help on it [http://ubuntuforums.org/showthread.php?p=2496843&posted=1#post2496843](http://ubuntuforums.org/showthread.php?p=2496843&posted=1#post2496843)

---

### Post by kilou on 2007-05-09
You seem to have compiled a Vanilla kernel and applied the Con Kolivas patch to it, what explain the name of the kernel (ck1). As in my situation there is no restricted modules that will match this kernel probabl just because of the name. This is why I've been looking into a way to symlink the original restricted module folders and files to something with the new kernel designation (see my previous post) but I still get the same error.

I don't know how and where the restricted driver manager looks for the restricted modules. Maybe the symlinks in my previous post would work but the manager still look at a list of installed packages and cannot find the restricted modules with our kernel designation. If we can find where the manager looks to check if restricted modules are installed, we can simply add a line to that file to trick the manager into thinking that our restricted modules are installed...and then it will use the symlinks to load them :KS 

Does anyone know if there exist a file that list all the installed packages? (I mean a file that is used by Ubuntu, for instance Synaptics, to know which package is installed etc. Not something you built so that you can reinstall the packages afterwards). Any such file somewhere?

---

### Post by kilou on 2007-05-09
OK I got something very interesting!!!!! I did **sudo gedit /var/lib/dpkg/status** and added a reference to a fake package called linux-restricted-modules-2.6.20.3-ubuntu1-custom in my case. I simply looked for the lines about linux-restricted-modules-2.6.20-15-generic (the original package) and copy/paste them and changed the reference as well as the version number with the new name. Now the restricted manager doesn't show any error and thinks that this package is installed :guitar: Possibly the file "available" in the same folder needs to be altered as well....

This doesn't mean it's working. The manager tell me that my hardware doesn't need any resricted drivers, which is true in my situation so I cannot really test if this works. Moreover I only did this mod in the status file but I had removed all symlinks previously (the ones mentionned in my previous post). Probably that in order for this to reall work, we must recreate the symlinks and do the mod in the status file. This way the status file will trick the manager into thinking the restricted modules for our custom kernel exists and then the symlinks will allow the manager to look into the original restricted modules to install them!!! 

However I'd need someone with an ATI or NVIDIA card (who need restricted modules) to test this and see if this works! It would be nice to test with a custom compiled Ubuntu 2.6.20 kernel and with a 2.6.20 Vanilla kernel to see if this makes any difference. This would be great because it would allow people to compile their own kernel but still use the restricted modules (if this works).

---

### Post by kilou on 2007-05-09
Rjwboys, if you need the restricted modules with your custom kernel could you please try the following to see if that works (this assumes that the missing package is linux-restricted-modules-2.6.20-ck1):

1) **sudo gedit /var/lib/dpkg/status** and copy the following at the end of the file then save it:

########### start copy here ########### 
Package: linux-restricted-modules-2.6.20-ck1
Status: install ok installed
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: 2.6.20-ck1
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-15-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
  - madwifi (Atheros)
  - fglrx (ATI)
  - nvidia
  - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.
########### end copy here ########### 

2) **sudo gedit /var/lib/dpkg/available** and copy the following at the end of the file then save it:

########### start copy here ########### 
Package: linux-restricted-modules-2.6.20-ck1
Priority: optional
Section: restricted/misc
Installed-Size: 41328
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20
Version: 2.6.20-ck1
Provides: nvidia-kernel-1.0.9631, nvidia-kernel-1.0.7184, nvidia-kernel-1.0.9755
Depends: linux-image-2.6.20-15-generic, linux-restricted-modules-common (>= 2.6.20), module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx | nvidia-glx-legacy | nvidia-glx-new, avm-fritz-firmware-2.6.20-15
Size: 16096180
Description: Non-free Linux 2.6.20 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.20 on
 x86/x86_64.
 .
 Currently the following modules are included:
  - madwifi (Atheros)
  - fglrx (ATI)
  - nvidia
  - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.
########### end copy here ########### 

3) In the terminal copy/paste these lines one at a time and run them:

cd /lib/firmware
sudo ln -s 2.6.20-15-generic 2.6.20-ck1

cd /lib/linux-restricted-modules
sudo ln -s 2.6.20-15-generic 2.6.20-ck1

cd /usr/share/linux-restricted-modules
sudo ln -s 2.6.20-15-generic 2.6.20-ck1

cd /var/lib/dpkg/info
sudo ln -s linux-restricted-modules-2.6.20-15-generic.md5sums linux-restricted-modules-2.6.20-ck1.md5sums
sudo ln -s linux-restricted-modules-2.6.20-15-generic.postinst linux-restricted-modules-2.6.20-ck1.postinst
sudo ln -s linux-restricted-modules-2.6.20-15-generic.postrm linux-restricted-modules-2.6.20-ck1.postrm
sudo ln -s linux-restricted-modules-2.6.20-15-generic.list linux-restricted-modules-2.6.20-ck1.list

4) Try to open the restricted drivers manager and see if it works (to see if it works you should try to install one driver. If the manager tells you that your hardware doesn't need any restricted driver it doesn't mean it is working!)

---

### Post by rjwboys on 2007-05-10
ok i will try this when i get home today thanks for the responce ill will let you know if this works
rjwboys aka richard williamson

---

### Post by rjwboys on 2007-05-10
i got your drivers doesnt need restrected drivers after that and i know that it does sinces its nvidia 




(edit) lol i didnt have the nvidia drivers installed and had to redo it after i got it installed and it worked it opened up with a menu 
Driver________________________________ Enabled_________Status
NVIDIA acceleated graphics driver_________ (checked)_______ (checked)In Use

---

### Post by kilou on 2007-05-11
OK but I would have assumed that the manager would allow you to install the nvidia drivers. Did you install the nvidia drivers yourself or through the manager? If you got the message "your hardware doesn't need restricted drivers" before installing the nvidia drivers then I guess this trick is not really working :( ....but I don't have experience with this because my computer doesn't need any restricted driver.

If you reopen the manager, can you unselect (disable) the nvidia drivers and see if it gets effectively uninstalled (I don't really know how you can check if the nvidia drivers is really uninstalled though..maybe look at hardware information)? If you can enable/disable the driver from the manager and if the changes are effectively applied then it means the trick is working.

---

### Post by rjwboys on 2007-05-11
what happened is that i had nvidia installed but it wasnt installed correctly and in xorg it was set as nv and so i sudo apt-get remove all of nvidia then rebooted into safe mode and ran envy reinstalled the restricted-manager as it got removed with nvidia and then added the info to the end just like you had except that i had to copy and paste from the files them self as i was getting parse errors with your code after that it worked ill try later to uncheck the file as im at work now

---

### Post by kilou on 2007-05-11
OK that would be interesting to know. But do you have a reliable way to know if the nvidia restricted driver is effectively uninstalled after you'll uncheck the mark in the manager? Does your xorg file mention what is the current display driver? If yes than just make sure that after unchecking the driver xorg gets a generic display driver and when you check nvidia back in the manager your xorg should mention nvidia again. If this happen then we'll know that this trick work and maybe we can use it for other kernel upgrades.

You compiled a Vanilla kernel from [www.kernel.org](www.kernel.org), right? It's nice if we can use Ubuntu restricted drivers with Vanilla kernels :)

---

### Post by rjwboys on 2007-05-11
well i was following a tut to make Ubuntu run better when i still had edgy that had me to download 2.6.20 and patch-2.6.20-ck1.bz2 and patch it and i didn't finish it as i was doing it over ssh from work and didn't want to reboot the computer etc. So i stopped and forgot about it a couple of weeks later i see in the update manager that feisty was released so i updated and when it did the update it saw the 2.6.20 which i have patched but didn't install and used it so thats how i got 2.6.20-ck1 lol well will post later when i get home and tried what you said

---

### Post by rjwboys on 2007-05-11
:popcorn: :guitar: :popcorn:  it worked it worked i click disable and it uninstalled it and had me reboot the computer which in turn brought the black bar on the right back then i went in and clicked enable and it installed nvidia and said to reboot and it got rid of the black bar on the right ... now if only i can get beryl or compiz working right i had beryl working on edgy but it stoped working when i upgraded to feisty:lolflag: and compiz works but doesnt have the decorations working :lolflag:

---

### Post by kilou on 2007-05-12
Great to read that this restricted modules trick does work :) I'll probably post a small HowTo for other people because I think many need to compile their own kernel (especially laptop owners to apply the linux PHC patch for undervolting) but would need the restricted modules to work.

What's the problem with Beryl? I have Feisty and Beryl works great for me. Have you checked if your xorg.conf file is correctly configured? I know that there are many things to add in that file for Nvidia card users. Do you launch emerald with **emerald --replace** command? Maybe the best is to completely uninstall Beryl after saving the configuration file and then reinstall it through synaptics in Feisty and folowing one of those HowTo for Nvidia users.

---

### Post by rjwboys on 2007-05-12
ok will try a compleat uninstall and reinstall....... lol apt seems to notice there isnt really a file for linux-restricted-modules-2.6.20-ck1   
dpkg: serious warning: files list file for package `linux-restricted-modules-2.6.20-ck1' missing, assuming package has no files currently installed.
but the restricted manager doesnt care:lolflag:


edit: i tryed to do an uninstall reinstall of beryl and beryl boots up but all i see is black and i notice the cube is working so all four sides is black and the top and bottom have the red diamond

---

### Post by kilou on 2007-06-01
Hi rjwboys,

could you please explain what exactly you had to do in order to have the restricted drivers manager working with your custom kernel after you modified the two files and applied the symlinks? You could post your comment on this thread as well:

[http://ubuntuforums.org/showthread.php?p=2761452#post2761452](http://ubuntuforums.org/showthread.php?p=2761452#post2761452)

Thanks

---

