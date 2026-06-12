---
title: "Dual Boot with Windows 11?"
date: 2021-10-06
forum: General Help
---

### Post by rhaes on 2021-10-06
Hello,

I can't seem to figure out how to get this done. I've googled it and a lot of sites said it is possible to install Kubuntu with Secure Boot on (so that it may be used with Windows 11) but whenever I start up the process, it tells me I need to set a password to install 3rd Party Softwares. I put down a password and then it just sits there. I'm clearly in need of some help. :-\"

If someone could help me set this up, that'd be really great and I'd appreciate the heck out of it. I use Windows to game and Kubuntu to write/study etc. My life needs Linux. Thanks!

---

### Post by QIII on 2021-10-06
Just to clarify:

Do you have Kubuntu installed and want to add Win11, or do you have Win11 installed and want to add Kubuntu?

---

### Post by dragonfly41 on 2021-10-06
If you have Windows 11 (apparently my humble Dell does not support it) then you can leverage WSL2 which is an instance of Ubuntu in full. WSL1 is just the bash version. In short, dual boot might not be needed.  But I prefer to stay outside the Windows realm and I use an external SSD for Ubuntu.

---

### Post by grahammechanical on 2021-10-06
What version of Kubuntu are you using? Old ISO images of Ubuntu and the flavours have been blacklisted in the secure boot database because of a security flaw in grub that was fixed and corrected in newer ISO images but of course could not be patched in ISO images that have already been downloaded.

Ubuntu and the flavours can be installed with secure boot enabled. Proprietary video drivers are another matter. And the matter cannot be rectified by Ubuntu developers but by the company producing the video card and the drivers.

I think that you may need to perform some action to self authenticate the 3rd party software. Not being a Windows user I cannot explain how to do that.

These might help

[https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029](https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029)

This link is very long and you have to scroll way down before you get to UEFI System - SecureBoot Enabled

[https://www.itzgeek.com/post/how-to-install-nvidia-drivers-on-ubuntu-20-04-ubuntu-18-04.html#Install_Nvidia_Drivers_from_Ubuntu_Repository_/_PPA](https://www.itzgeek.com/post/how-to-install-nvidia-drivers-on-ubuntu-20-04-ubuntu-18-04.html#Install_Nvidia_Drivers_from_Ubuntu_Repository_/_PPA)

They may need some revision for Windows 11

Regards

---

### Post by oldfred on 2021-10-06
Is the password you are entering your Ubuntu password or the MOK or UEFI machine owner key  which is only required with proprietary drivers like nVidia and some Wi-Fi drivers. 
[https://wiki.ubuntu.com/UEFI/SecureBoot#Security_implications_in_Machine-Owner_Key_management](https://wiki.ubuntu.com/UEFI/SecureBoot#Security_implications_in_Machine-Owner_Key_management)

Ubuntu uses the Microsoft key for UEFI Secure Boot. 
But Ubuntu cannot sign other vendors drivers as they are provided just as a binary blob. But a user can sign those drivers if he believes they are safe. So if you have nVidia you need to create the MOK, so driver can be used.

It does not look like you have to use UEFI Secure boot.
[https://support.microsoft.com/en-us/topic/windows-11-and-secure-boot-a8ff1202-c0d9-42f5-940f-843abef64fad](https://support.microsoft.com/en-us/topic/windows-11-and-secure-boot-a8ff1202-c0d9-42f5-940f-843abef64fad)
> While the requirement to upgrade a Windows 10 device to Windows 11 is  only that the PC be Secure Boot capable by having UEFI/BIOS enabled, you  may also consider enabling or turning Secure Boot on for better  security. 

---

### Post by rhaes on 2021-10-06
> **QIII said:**
> Just to clarify:

Do you have Kubuntu installed and want to add Win11, or do you have Win11 installed and want to add Kubuntu?

I'm sorry, I should have specified. I already had Kubuntu with my prior Windows 10 via Dual Boot, but now I just want to re-install over old Kubuntu with a new one, with Secure Boot enabled so it all works together. Windows 11 is already installed.

---

### Post by rhaes on 2021-10-06
> **oldfred said:**
> Is the password you are entering your Ubuntu password or the MOK or UEFI machine owner key  which is only required with proprietary drivers like nVidia and some Wi-Fi drivers. 
[https://wiki.ubuntu.com/UEFI/SecureBoot#Security_implications_in_Machine-Owner_Key_management](https://wiki.ubuntu.com/UEFI/SecureBoot#Security_implications_in_Machine-Owner_Key_management)

Ubuntu uses the Microsoft key for UEFI Secure Boot. 
But Ubuntu cannot sign other vendors drivers as they are provided just as a binary blob. But a user can sign those drivers if he believes they are safe. So if you have nVidia you need to create the MOK, so driver can be used.

It does not look like you have to use UEFI Secure boot.
[https://support.microsoft.com/en-us/topic/windows-11-and-secure-boot-a8ff1202-c0d9-42f5-940f-843abef64fad](https://support.microsoft.com/en-us/topic/windows-11-and-secure-boot-a8ff1202-c0d9-42f5-940f-843abef64fad)

It's different from my log in password for Ubuntu, for extra security. When I started the Kubuntu install, it asked me to input one. I wrote it down and everything, but the system just hung there. I had to force quit it there. I tested it without Secure Boot enabled, and the install went through like normal (which is obviously not what I wanted so I just erased it to start again). 

I'll read the link now, thank you!

> **QIII said:**
> Just to clarify:

Do you have Kubuntu installed and want to add Win11, or do you have Win11 installed and want to add Kubuntu?

I'm sorry, I should have specified. I already had Kubuntu with my prior Windows 10 via Dual Boot, but now I just want to re-install over old Kubuntu with a new one, with Secure Boot enabled so it all works together. Windows 11 is already installed.

I'm using the latest LTS for Kubuntu, which is 20.04.3 LTS. I made my bootable USB via Rufus, on a 16GB USB.

EDIT

I'm sorry, something got crossed up and I accidentally double posted. My bad, guys.

---

### Post by oldfred on 2021-10-06
Many systems need UEFI firmware update & if SSD, SSD firmware update.

Do not know Windows 11, but both 8 & 10 have fast startup which sets hibernation flag and prevents the Linux NTFS driver from seeing the NTFS partitions. You need to make sure fast start up in Windows is off. Note that Windows updates often turn it back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

