---
title: "Grub installation failed dusing install"
date: 2018-04-28
forum: General Help
---

### Post by linuxnovice on 2018-04-28
Hello,

I'm trying to install Kubuntu 18.04 on my system. Info about my system:

[LIST]
[*]2 disks for storage 250 GB SSD and 1 TB HDD
[*]Windows 10 installed taking 120 GB SDD
[*]Partitioned HDD into 350GB (for Windows) and 650 GB (for Kubuntu)
[*]Installed Kubuntu 18.04 on SSD with 20GB on /, rest on /home, and HDD space on custom mount point /storage
[*]
[/LIST]

I used the minimal install option and the installation ran smoothly. However, at the end of the installation I got a message saying "Grub installation failed" (check screenshot). This is my second attempt installing. I'd like some help in figuring this out. I believe that only Grub did not get installed and Kubuntu installed without problems. When I restarted my computer last time, it directly booted into Windows. However, through the LiveCD, I could see that all the partitions were intact. So I'm guessing that Kubuntu is still residing in the disks, its just Grub has failed to installed preventing me from booting into Kubuntu. Am I right about this? 

FYI:
[LIST=1]
[*]I'm posting this message from the LiveCD.
[*]Fast startup is tunred OFF in Windows 10
[*]Motherboard ASUS z77 Extreme4 has SECURE BOOT DISABLED.
[*]
[/LIST]

Please let me know if you need additional information. I'll try to be on LiveCD until I get can get some help. Any help is appreciated.



Thanks.

EDIT1:
Found out that a bug was filed for this [here]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1767602").

---

### Post by linuxnovice on 2018-04-28
I found out that my Windows machine is booting into Legacy BIOS. I don't know if thats relevant or not.

---

### Post by yancek on 2018-04-28
> I found out that my Windows machine is booting into Legacy BIOS. I don't know if thats relevant or not. 		

Yes, it is.  If your windows is installed Legacy, then Kubuntu needs to be installed Legacy.  Did you do that?  If you can boot the Kubuntu DVD/flash drive, do that and open a terminal and run the command below to see if you have an EFI partition, if you do check to see what is in it.  If there is a microsoft folder and an Ubunt or Kubuntu folder, then you have UEFI.  The Ubuntu site below has some useful general information on UEFI dual booting.  If you do not have a windows UEFI, the you either installed Kubuntu Legacy or failed to install the Grub bootloader properly.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by linuxnovice on 2018-04-28
Yes. I apparently used the UEFI version of Kubuntu install. I changed that and everything went fine. Lesson learned is use the same boot mode as Windows is using for installing when dual-booting.

---

