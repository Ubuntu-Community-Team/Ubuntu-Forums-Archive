---
title: "Removing a test install. Need GRUB advise."
date: 2013-11-07
forum: General Help
---

### Post by Razmear on 2013-11-07
Here is the current setup. 
Disk 1 (500g)
Partition 1 400g Kubuntu 12.4.3 32bit - Keep
Partition 2 80g Kubuntu 13.10 64bit- Test Install to be removed.
Disk 2 (640g)
Partition 1 Kubuntu 13.10 64bit - Using now

My 500g drive started to get bad sectors, so I ordered the 640g and while waiting for it to arrive did a test install of 64bit Kubuntu 13.10 in a new partition of that drive.
Now that the 640g is here, and 13.10 installed on it, I no longer need the second 13.10 install on the old 500g drive. I'll keep the 12.4.3 32bit install just incase it's needed for backwards compatiblity. 
My goal is to safely remove the 13.10 test install without screwing up GRUB and use that space for storage. Seeing how I've trashed GRUB in the past, if someone could post the best method of wiping/formatting the 80gig partition on Disk 1 and removing it's entry from GRUB I'd appriciate it. The GRUB load screen has renamed the test install to Ubuntu 13.10 and calls the newest install Kubuntu, which should make them easier to identify. 
Thanks for any help,
eb

Update:
Edited Grub with: 
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
will mark solved after reboot if all is good.

---

### Post by oldfred on 2013-11-08
While you can use a live installer or even your other hard drive to mount your 32 bit install and install its grub to the 500GB drive, it is just easier to boot into your 32 bit install and run this:

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

    
Do you have the grub for the new install of Kubuntu on the 640GB drive in the MBR of the 640GB drive? If not boot into it first and run the same commands as above but with sdb as install location first.
You will want BIOS to boot from the new drive as default.

You want each install of Kubuntu to be bootable from the MBR of the same drive.
Then you can install gparted into your Kubuntu and use it to modify/erase or do whatever you want. You do not have to use live installer unless you want to work on the system you boot, so you can work on any other drive without issue if partitions are not automatically mounted.

---

