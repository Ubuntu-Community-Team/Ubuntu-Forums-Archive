---
title: "Dell G3 not booting from Ubuntu"
date: 2019-06-17
forum: General Help
---

### Post by visionarily on 2019-06-17
Hello I have a Dell G3 that i'm trying to install any version of ubuntu on, however i am constantly having errors doing this. I have tried with Ubuntu budgie 18,19.04, Normal Ubuntu 18,19.04, Ubuntu Mate 18,19.04, Kubuntu, and xubuntu but I just can't seem to be able to install onto my laptop. I either get a freeze on the installer boot-up, a kernel panic, an input/output error on my ssd, or the installer was unable to install the bootloader. Yes I have tried manually making a /boot partition for the bootloader. I know the SSD is not the problem as it worked in one of my other pcs perfectly fine. I have enabled a legacy boot in the bios, but whenever i try to enable legacy from the ssd, the bios can't detect a bootloader even if the install seemed flawless. I'm not sure if the fact that the Dell G3 uses the intel igpu while also having a 1050ti in the system is causing the installer to break or if I have something wrong with my bios revision. I could really use some help with this one.

---

### Post by yancek on 2019-06-17
You make no mention of any other operating system so does that mean you are using the 'Erase disk and install Ubuntu' option?
Why are you creating a separate boot partition?  In most cases it is not necessary and complicates things for new users.
Are you using UEFI?  Do you already have an EFI partition or do you create one during the install?
How are you trying to install?  Are you using a usb/flash drive?  If so, how (what software) did you create it? 
Did you do the install in Legacy mode?  Do you have an EFI partition?  Are you using GPT disks?

---

### Post by jglen4902 on 2019-06-17
You made no mention of another OS.  Assuming this is intended to be a single boot, Ubuntu machine, there should be no reason to use Legacy mode to install Ubuntu.

Enter the UEFI, change the boot mode to UEFI, set Secure Boot to disabled, and make sure AHCI is set.  With the USB Live installer drive attached, make sure it shows as being the first drive in the boot order.  Leave the USB drive attached and reboot the machine.  The USB drive should boot.  When you get to the install options screen, select the "Something else" option so the you can control the disk partitioning.  Set a new partitioning table to GPT, then make you partitions as you want with the first partition being the ESP (EFI System Partition).  The ESP for a single boot machine should be between 200 - 500MB, although the boot files woun't take up nearly that much space.  Then set the remaining space to whatever sizes you want for the / partition, the /home partition, and if you want the SWAP partition.  Continue with the install

---

### Post by visionarily on 2019-06-17
The Dell G3 originally had Windows 10 on it but I went to ubuntu thanks to driver issues in Windows. Also I am not using the 'Erase disk and install Ubuntu' option because if I choose that the installer will fail to install the grub bootloader. So I have to choose the 'Something else' option and create an ext4 partition for the bootloader and OS. I also have to use UFEI as changing to a legacy boot mode in the Dell bios is impossible thanks to the option being greyed out. But no, I don't have any UFEI partitions on my SSD anymore. I am using Rufus to put my ubuntu installations onto a USB stick since the G3 has no DVD drive and I don't have an external drive. I have tried multiple USB sticks with the installs, however it doesn't seem to change anything. I've also never had any problems with Rufus and have used it for many successful OS installs, so I don't think that's the problem here.

---

### Post by jglen4902 on 2019-06-17
Rufus is a fine application for creating reliable, bootable USB drives - I agree that there should be no problems from that.

I always do clean installs, and have a process with UEFI "BIOS" installs of Linux that has worked well.

With UEFI, when there is a choice between booting in UEFI mode or booting in Legacy, I always set UEFI.  I also always disable Secure Boot.  I always check the settings in UEFI with the USB Linux boot drive attached so that it shows up in the boot disk list, and I always set the USB drive to the first bootable disk.  Then I save the UEFI "BIOS" settings, and with the USB drive attached, I reboot the machine.

Once the USB drive boots the system and the Live installer shows up, I just follow the install process screen by screen - nothing automatic.  I create the ESP partition, and eliminate any other system files or OS that may exist.  The ESP shows up as the first partition on the first system drive (**_/dev/sda1_**), and that's where the Grub boot files need to be installed.

This process works every time, since I've been using UEFI motherboard systems.  To the best of my knowledge, Dell UEFI allows choosing for UEFI boot and allows disabling Secure Boot.

---

### Post by oldfred on 2019-06-17
Most Dell need UEFI update and if SSD, firmware update.

You also need to make sure your have changed UEFI setting for drives from RAID or Intel RST to AHCI. If dual booting withc Windows install AHCI driver first.
If NTFS partitions on drive, make sure you have turned off Windows fast start up which sets hibernation flag and prevents the Linux NTFS driver from seeing the NTFS partitions.

It looks like your model includes nVidia, so you will need nomodeset boot parameter.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

Issues are common by brand, bigger difference within brand by Intel or AMD based systems.
       
 Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560)

---

