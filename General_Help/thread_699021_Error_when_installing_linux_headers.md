---
title: "Error when installing linux headers"
date: 2008-02-16
forum: General Help
---

### Post by fissionmailed on 2008-02-16
I keep on getting this error and I have no idea what to do.

```
sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm assuming this is somewhat important??  It has also been acting funny too, programs freezing etc.  This may be related or have nothing to do with it.  Seeing as in it's in boot I'm assuming these aren't related but I'd thought I'd just throw them out there to make sure.  When installing the updates for the new headers there was also an error too. hhhmmmmm I think it was the same thing with files in /boot/, but I'm not too sure.

I'm running a 64 bit version of ubuntu 7.10. I could reinstall, but I've gotten everything to work and installed a VM and all so I'd rather not.

Any ideas how I could fix this?:confused:

---

### Post by scottbporter on 2008-02-16
I have no idea how to fix. I have had problems as well, after headers upgrade. First, I put my computer in hibernation mode. When I re-booted, the partion could not be recognized by the computer. I ran gparted boot disk, it was not recognized as ANY type of partition. I ran grub restorer, no help. I re-installed. Next time I updated headers I lost the resolution settings. I run an ATI Radeon Xpress 200. No way have I found to resolve the issue, always boots in low resolution mode and I need 1440x900. I will need to re-install again! I guess I will just turn automatic upgrades off. Actually Feisty was better. I can't get 3d graphics to work with gutsy when it did with feisty. I may go back to it or swith distros until ubuntu gets worked out.

---

### Post by zanak on 2008-02-16
I don't know if it solves your problem but it seems that you need to install getopt. use synaptic for that

---

### Post by fissionmailed on 2008-02-17
> **scottbporter said:**
> I have no idea how to fix. I have had problems as well, after headers upgrade. First, I put my computer in hibernation mode. When I re-booted, the partion could not be recognized by the computer. I ran gparted boot disk, it was not recognized as ANY type of partition. I ran grub restorer, no help. I re-installed. Next time I updated headers I lost the resolution settings. I run an ATI Radeon Xpress 200. No way have I found to resolve the issue, always boots in low resolution mode and I need 1440x900. I will need to re-install again! I guess I will just turn automatic upgrades off. Actually Feisty was better. I can't get 3d graphics to work with gutsy when it did with feisty. I may go back to it or swith distros until ubuntu gets worked out.

hhhhmmmm That's not too encouraging seeing as in I have an ATI graphics card too. hhmmm

zanak:  I'm doing that now and then I'll check too see if all works.

Edit. when trying to install it, I get this error

"E: linux-image-2.6.22-14-generic: subprocess post-installation script returned error exit status 2"


hhmmmm

---

