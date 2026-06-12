---
title: "Removing Grub completely"
date: 2013-06-23
forum: General Help
---

### Post by tdp2010 on 2013-06-23
I just made a bit of a serious mistake.  I was installing a copy of Xubuntu 10.04 from the CD to a flash drive (sdb) plugged into my computer, and I did not unplug my internal hard drive (sda) first.  Now, if I remove the flash drive while the computer is shut down, it refuses to boot from the internal drive when switched back on.  Instead, it gives me a "no such device" error message followed by a string of numbers and requests a "grub rescue >" command.  If I plug the flash drive back in and restart, it takes me to the typical Grub boot menu and I have to select my internal drive manually from there.

So, how do I remove Grub completely?  Completely in the sense that my computer will automatically boot properly to the sda drive again, AND that the Grub menu will be removed so that I don't have to make a selection or go through that step.  I really would like to avoid having to keep this flash drive plugged in all the time just so I can use my machine.  I'm assuming it's not as simple as sudo apt-get remove grub.

I'd really appreciate some help in fixing this as soon as possible.  Thanks.

---

### Post by oldfred on 2013-06-23
#reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


What do you have on your internal drive? Windows? Then you need a Windows boot loader in the MBR of sda.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or you can use a Windows RepairCD.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by tdp2010 on 2013-06-23
My internal drive is /dev/sda and I have Xubuntu installed on that as well.  So basically I should just reinstall grub on it with the flash drive removed from the system and that will overwrite the previous installation?

---

### Post by grahammechanical on 2013-06-23
The Ubuntu installer will install Grub to the MBR of some hard disk. The default is sda. when the machine is switched on Grub will look for its configuration files in /boot/grub/grub.cfg on a partition on sda. But in your case /boot/grub/grub.cfg is on the Flash drive. So, Grub looks for sdb but you have unplugged the flash drive. That is why Grub is saying "no such device" and begging to be rescued.

So, boot into Xubuntu, eject the Flash drive, open a terminal and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That should re-install Grub into the MBR of sda but looking to /boot/grub/grub.cfg on sda.

What you next need to do is use the BIOS to boot into the flash drive and then run

```
sudo grub-install /dev/sdb
```

Other wise you may not be able to boot into the flash drive.

Regards.

---

### Post by tdp2010 on 2013-06-23
That worked perfectly, thanks so much for the help.

---

