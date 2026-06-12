---
title: "Virtualization - dual boot system - without disk image"
date: 2007-05-23
forum: General Help
---

### Post by alperyilmaz on 2007-05-23
Hi,

I have a simple situation for virtualization but I couldn't locate the best software. My case is;
- I have single machine with windows XP and Ubuntu dual boot. 
- I'd like to run Ubuntu as main OS and need to run Windows occassionally
- Instead of booting to Windows to each time, I need virtualization (I don't prefer Wine)
- There are many options there, such as;
........ Xen, Qemu, VMware, Virtualbox, rdesktop, kvm, VNC server, Seamless

- I gave VMware a try but here are the problems; you make a disk image of your existing Windows and that image is used for virtualization. But, if the partition your windows reside in is 30GB then you need extra 30GB for that image and most importantly, all the changes you made during virtualization stays in that image, your existing Windows system becomes out-dated after every virtualization session. I can try VMware again if it's possible to take an image of Windows or System folders, not whole partition. Is that possible?

- I know Virtualbox won't work for me, because I cannot make a clean install of Windows. I need to access my existing, 2-year old Windows system.

So, my question is, what is the best virtualization technique to access an EXISTING Windows OS? On top of that, if I install a software or change settings during Windows virtualization, I want to have those changes kept when I restart computer and boot into Windows.

Is this possible? Do all virtualization softwares create and use non-updating images?

thanks..

---

### Post by Barrius on 2007-05-23
As far as I know, no Virtualization solution allows you to use your existing Windows as the Virtual (although WMWare will make an image from your existing Windows installation).

If you only need to use Windows occasionally, use VMWare to save your existing install to an image, test it, and if everything is ok then (Backup!!) and delete your Windows installation, only running Ubuntu and a virtual Windows.   Any changes made in you virtual Windows installation will be saved just as they are done now.

Several of the Virtualization programs allow you to save a copy of the image in case you need to revert back.    In some cases this is done to ensure that Windows virtualizations can be reverted to a previous "clean" version in case of malware/virus infestations.

---

### Post by transparent9 on 2007-05-25
This howto seems to describe what you want: running Windows off an existing partition in VMware

[http://ubuntuforums.org/showthread.php?t=380699&highlight=howto+vmware+windows+existing](http://ubuntuforums.org/showthread.php?t=380699&highlight=howto+vmware+windows+existing)

---

