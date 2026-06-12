---
title: "Safely removing the Ubuntu HDD and switcing from GRUB2 to Windows 7 Bootloader."
date: 2014-05-01
forum: General Help
---

### Post by dragonator2 on 2014-05-01
Hello.

Because of constant hardware compatibility issues I have remained for years a primarily Windows user, but hopeful Ubuntu migrant. Unfortunately, my hardware curse keeps causing trouble. Here is my current, somewhat delicate situation with which I need support:

I have a desktop with multiple HDDs and one SSD. I have Windows 7 installed on the SSD and have installed Ubuntu as a test on an old 40GB IDE HDD. This was supposed to be a temporary arrangement in order to test hardware issues. I have installed Ubuntu fully on the HDD and managed to set up a GRUB2 boot loader to facilitate dual boot. 

The problem now is that I need to safely remove the Ubuntu HDD. When I have removed it and chose the option to boot from the SSD, no boot loader was detected. I need some advice on how to safely remove the HDD and switch back to Windows 7 boot loader, with the possibility to reinstall the HDD at a later time and dual boot with Ubuntu again. The SSD needs to be the primary boot device and Ubuntu will need to be installed on a 2nd HDD, which will be transferred later to another system, somehow. (I'd like to clone the entire Ubuntu OS HDD and transfer the info to another SSD in the 2nd system, or at least transfer the config info and personal data into a fresh copy, to make the transition seamless somehow. I haven't figured out the details yet, but it's besides the point now.)

The simplest way I can see to do this would be to remove the Ubuntu HDD and run the Windows 7 DVD repair wizard to restore the boot loader. Are there any other, safer ways to do this?

Thanks.

---

### Post by oldfred on 2014-05-02
You can use Boot-Repair, but do not run its auto repair. That installs grub to every MBR.
You can choose advanced and choose Windows and install the Windows boot loader to the Windows drive.
You should install grub to Ubuntu drive also.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
But grub remembers where you installed it, so on a major grub update it may reinstall to the remembered location. Best to use dpkg to install to correct drive and update it saved location.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
If installing to a second drive, best to use Something Else and at bottom of partitioning screen is a combo box on which drive to install grub. It defaults to sda, just change to sdb, or whatever drive you are installing into.

---

