---
title: "Help to resolve incorrect GRUB setup with multiple distro install"
date: 2016-03-05
forum: General Help
---

### Post by Neil_McMe on 2016-03-05
Not sure if this is the correct Forum for this, if not apologies and please advise where would be better to ask for help.

I've installed Ubuntu 14.04 LTS as the main OS on a USB HDD attached to a laptop. Windows 10 is still on the laptop internal HDD, and just for fun i installed a few other LInux distros also on the USB drive. In general terms it all works. Ive been fidiling with PCs for years, back to MSDOS, so im not a total newb but i am quite new to linux.

I have used a partition set up on the USB HDD to separate each distro but because Ubuntu is the main OS it has separate primary partitions for BOOT, HOME & ROOT. The SWAP partition and a number of 20Gb "distro" partitions are set-up as logical drives in an extended partition.

The setup all works fine, but the problem is i totally screwed up with Grub, i assumed that with each new distro install Grub would find the original Ubuntu Grub boot files in the Ubuntu BOOT partition and the new disto would just be added to the Ubuntu Grub setup. But it seems that each distro does its own grub install to its own root partition which then becomes the master grub. It took a while for the penny to drop so i now have 4 or 5 distros installed with Open SUSE currently in charge of Grub.

I have trawled around the net, looked through Ubuntu grub info and had a look at the Grub home site, but cant find anything very helpful to resolve what i have created.

I want to get Grub back Under control of the original one installed with Ubuntu 14.04 but i really dont know where to start. From what i have read i may have issues with the linux kernel?? and MBR?? on the USB drive, but i'm not really sure.

Can anyone point me in the right direction ?

Neil....

---

### Post by Dennis N on 2016-03-05
Just boot your system to Ubuntu 14.04 LTS and reinstall grub to the same location you originally did, like /dev/sdb. After install, run sudo update-grub.

In your terminal:
```
sudo grub-install /dev/sdb
sudo update-grub

```

Reboot, and you should again be using the grub menu of Ubuntu 14.04 to boot the others.

---

### Post by oldfred on 2016-03-05
You also have some other issues.
Each install on kernel or grub update may reinstall grub to MBR.
And each install runs its update of grub so menu have newer kernel, but you have to boot into Ubuntu and run its sudo update-grub to get newer entry from other install.
If Debian based, you should have a link to newest kernel in / and can use link to boot. But you have to manually create your own entry in 40_custom. Do not know of other distributions do something similar or not. But it allows reboot of Ubuntu's grub to immediately load new kernel in other install, without have to boot Ubuntu just to update grub menu.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by Neil_McMe on 2016-03-06
oldfred - Once i get grub back under Ubuntu control, Based on a magazine article (Linux Format 208) i think i need to go through each other distro and confine their grub versions to their own root partitions. Then when installing future distros i need to manually set grub to install within the root partition of the new distro.

Dennis N - Tried grub-install /dev/xxxx as sudo with full install and with a live version of Ubuntu 14.04 both failed but with different errors,

FROM THE LIVE BOOT,
~ :$ sudo grub-install /dev/sdb1
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
~ :$ 

FROM THE FULL INSTALL BOOT,
~ :$ sudo grub-install /dev/sdb1
Installing for i386-pc platform.
grub-install: warning: Filesystem `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
~ :$ 


I dont know where the 'ext2' comes from because dev/sdb1 is format to ext4.

I'm starting to think the brute force approach of re-format and start from scratch, might be the way forward, but i'm open to any other suggestions.

Thanks.....

---

### Post by grahammechanical on 2016-03-06
With grub-install /dev/sdb1 you are installing it to a partition. The advice from Dennis N was to install Grub to the MBR of sdb

```
sudo grub-install /dev/sdb
sudo update-grub
```

It works for me in this situation. It is what I would have recommended. I saw no need to add to what was the right answer. For myself, when another Linux install takes over the boot menu I simply load into my working Ubuntu and run those two commands. It works every time. It is not a fix once, fix all time solution. But it is an uncomplicated solution.

Regards

---

### Post by Dennis N on 2016-03-06
> FROM THE FULL INSTALL BOOT,
~ :$ sudo grub-install /dev/sdb1
Installing for i386-pc platform.
grub-install: warning: Filesystem `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
~ :$ 

You are installing grub to a wrong location. The command should be:

```
sudo grub-install /dev/sdb
```
with no number after sdb. This installs to the MBR of sdb. With an MS-DOS partition table, grub has to be installed to the MBR of a disk (using /dev/sdb1 installs grub to the first partition where it can't be accessed by the BIOS and won't boot). 

This kind of setup means you select sdb as the boot device in the one-time boot menu to get to the Linux OSes you have on sdb. I assume that is the kind of setup you originally made?

---

### Post by oldfred on 2016-03-06
Also the /cow means you used the live installer. Instructions were from inside the actual Ubuntu install, so you did not have to mount the partition with the install
If using live installer you have to mount the install and then install grub.

With multiple drives and/or multiple installs best to use Boot-Repair and run its Summary Report just to know what is installed where.
It uses bootinfoscript as part of the report but if using a script or just want a terminal version of the most critical data you can just run the bootinfoscript. I occassionly run the Boot-Repair summary report and include new copy of bootinfoscripts report with every rsync backup.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info
[/URL]
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by Neil_McMe on 2016-03-06
Thanks to all, once i opened my eyes and actually entered the correct commands, Ubuntu Grub is now back in charge.

---

