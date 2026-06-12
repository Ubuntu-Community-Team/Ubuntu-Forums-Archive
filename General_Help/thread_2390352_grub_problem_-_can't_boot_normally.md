---
title: "grub problem - can't boot normally"
date: 2018-04-28
forum: General Help
---

### Post by raysa on 2018-04-28
On my main desktop, which runs xubuntu 16.04, I downloaded a xubuntu 18.04 ico to install it on a laptop. I copied if from my download folder to a usb stick and then ejected and removed the usb stick. I didn't want to interfere with my 16.04 set-up and didn't ask for the 18.04 to be installed on the desktop, but it seems to have messed up the grub.
Now ... on booting up the desktop, up pops the 18.04 live trial, with no access to my 16.04 installation. When I interrupt the boot with f12, the options do not include the installed 16.04 - only the options to try 18.04 without installing it, or installing it.
How can I get back to firing up my 16.04 set-up with all its content?
Thanks.

---

### Post by Buntu Bunny on 2018-04-28
You might need to reinstall grub -> [https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

---

### Post by raysa on 2018-04-28
I looked at the Grub2 installing link above but had trouble identifying quite what to do. Rummaging around the file system of the trial 18.04 distro that boots up, I find it contains a volume in "Devices" which if I mount it, contains my entire 16.04 system as if it was in a folder on an external drive. So is it a grub problem after all?  I need that device volume to be seen as the main installation and booted accordingly, but I'm rather out of my depth here and would welcome clear instructions. Thanks.

---

### Post by yancek on 2018-04-28
How did you 'copy' the 18.04 iso to the usb stick and are you sure it is on the usb stick.  If you removed the stick, there is no way 18.04 would show.  So what method did you use to create a bootable usb to install 18.04 as copying it to a usb won't do it?  Is your Xubuntu an EFI install or Legacy/MBR?  Might be best to get boot repair from the link below and run it, make sure you select only to Create BootInfo Summary option and post the link with the output here for others to review.  Best to use the 2nd option to get boot repair.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by raysa on 2018-04-28
Thanks. I used the "create start-up disk" facility which was in my 16.04 'system' area to load the ico from my 'downloads' directory to the stick. Yes it ended up on the stick and it boots the 18.04 trial on the laptop I wanted it for (although the installation hangs on "installing the grub2 package, but that's another tale of woe - my focus for now is getting my desktop working again). 
Sorry, I don't know terms EFI or Legacy/MBR so I can't answer that question. 
I've done the boot repair thing and the report is at [http://paste.ubuntu.com/p/WzgKGbwsrX/](http://paste.ubuntu.com/p/WzgKGbwsrX/)
Thanks again.

---

### Post by oldfred on 2018-04-28
You have BIOS/MBR configuration. 
But you show two boot flags on sda,both sda1 & sda2. Only one active partition or partition with boot flag per device. So remove boot flag from sda1.
You can use Windows and its set active command (do not know off version), gparted, Disks, or command line to change boot flags.

Grub does not use boot flag, but Windows requires it on the partition with its boot files, your sda2.

Since both your Windows & Ubuntu installs are in BIOS boot mode, you need to always boot Windows repair disks or Ubuntu live installer for repairs in BIOS boot mode.
You booted in UEFI mode. See line 2700 in report.
So you do have newer UEFI hardware, but the older BIOS/MBR configuration.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations


[/URL]

---

### Post by raysa on 2018-04-28
Thank you. I'm unfamiliar with some of this terminology, but I should probably point out that I very, very seldom use Windows on this machine. It always fired up Xubuntu as default and I only ever interrupted the start-up to launch Windows if I had special reason to, which was hardly ever, and I'd like it to remain like this. The UEFI thing must have arrived when I downloaded the 18.04 ico for my new laptop (how I wish I'd downloaded it directly to the laptop instead of involving my desktop!!).  Is there a way I can revert to booting into the original 16.04 set-up as default and getting rid of whatever happened when I created the 18.04 stick?

---

### Post by raysa on 2018-04-29
I'm getting a bit desperate with this. I used gparted to remove the boot flag in SD1 as suggested, but to no effect - the computer still boots into the 18.04 live user trial, and the initial boot options only show the live trial or installation options - no option for my 16.04 installation (although that part of the hard disk is shown as an unmounted media device). The 'install 18.04' option said I could install 18.04 alongside my existing 16.04 and would get the option of which to choose when booting, so I thought that would enable me to get operational again and I proceeded. But then I got a message "grub-efi-amd64-signed package failed to install" 
I need to revert to booting into the original 16.04 set-up and getting rid of whatever happened when I created the 18.04 stick.

---

### Post by raysa on 2018-04-29
Yet another stumbling block ... from reading some of the links above I tried to reinstall grub2 using sudo grub-install /dev/sda, but I got the message "failed to get the canonical path of '/cow'.

---

### Post by oldfred on 2018-04-29
/cow is the installer. Or copy on write.
So you can not install grub to installer is it is not updateable.

If manually updating you have to mount your partition (& /boot if separate) and then install grub.
Often easier to use Boot-Repair as it can also run other repairs (but not most Windows repairs).

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

#Confirm partitions:
sudo parted -l
# mount partition that is /

 sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by raysa on 2018-04-29
Many thanks oldfred ,,, Boot-repair has got me back working with all intact.

---

