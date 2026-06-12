---
title: "Changing the order of selection in Grub"
date: 2017-07-11
forum: General Help
---

### Post by robelli on 2017-07-11
I am running Ubuntu 16.04 Mate and recently installed Mint 18.2 alongside . When the computer boots up it always selects Mint which is the first entry . I have been trying everything that has been said to change the order so that Ubuntu Mate is the OS selected . Consequently I now have for files in /etc/default/grub each with a different GRUB_DEFAULT in them but it still comes up with Mint . How do I get rid of those extra files and just keep one .

---

### Post by oldfred on 2017-07-12
You have two installs and two versions of grub. On major grub updates, each may reinstall its version as new boot loader in MBR if BIOS or ESP - efi system partition if UEFI.

You can quickly make Mate first in boot order, by just booting into Mate and reinstall grub to MBR if BIOS boot.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub 

    
But that only temporarily resolves issue.
Do not know Mint, but expect this works in it also:
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643) 
    
If newer UEFI may be a bit more complex.

But I have several installs and os-prober can take a while. And to get second installs' boot entry updated to new kernel requires two updates one in each install. Often easier to boot partition using links that are in / (root) to newest kernel and turn off os-prober.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by robelli on 2017-07-23
Thank you Oldfred. Apologies for taking so long to reply . It seems a lot of work to do and beyond me . I have reinstalled Mate only and all is now ok. I seem to remember that some time back it was just a simple matter to change to order of the operating system but now they have made it so complicated it is not for me to play around and break my system. A shame really . Cheers

---

