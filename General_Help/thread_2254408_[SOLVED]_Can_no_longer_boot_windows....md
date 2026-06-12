---
title: "[SOLVED] Can no longer boot windows..."
date: 2014-11-27
forum: General Help
---

### Post by Andrew_Salter on 2014-11-27
So I've run into a bit of a problem. I didn't have a USB drive or a blank DVD so I tried a bit of a work around... I created a 2gb partition in Windows, used the universal usb installer from PendriveLinux and installed the installer ISO to the newly created partition. I then used EasyBSD to add this partition as an entry for the bootloader. So far so good, the installer ran. But, as I realised, I can not create partitions for the install when running the installer of the same disk as what I will install on. So, I decided I would go back into Windows and create the partitions there. This was where I ran into another problem. I can no longer boot back into my Windows install! The boot manager option to select the partition to boot from does not show up. So all I can do is boot back into the installer. I can however, boot into the live CD mode. Any suggestions on how to fix this? I was thinking of maybe installing GRUB 2 bootloader?

Or is there someway I can make my Windows partition the default boot partition from within the Linux live CD mode?

SOLVED: Found a external hard drive and installed a boot loader.

---

