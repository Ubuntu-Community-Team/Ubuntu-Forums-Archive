---
title: "Installed Ubuntu alongside windows, now I get no boot menu and neither boot."
date: 2017-11-19
forum: General Help
---

### Post by bennk on 2017-11-19
Hello, I'm a new ubuntu user and I'm having some difficulty...

I'll tell the whole story.

I decided to install ubuntu alongside windows so I made a partition in my hard-drive in windows (10) that I would install ubuntu to. All went well except when I turned on my PC it never gave me any boot menu and would boot straight to windows. I googled how to fix this and I came across a website ( [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/) )that said to enter this command in cmd in windows 

```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

Unfortunately for me I should have read the article comments because this didn't fix anything, infact it made made matters worse. Now when I turn on my laptop it doesnt boot to windows or ubuntu, instead it goes straight into some Dell hardware scanning mode because it says my laptop is having problems booting.

After poking around for a while in the BIOS I am able to boot to ubuntu if I go into 'Boot Options' and choose to boot from the harddrive, but only that way, if I let the PC do its thing it goes into the Dell repair thing I mentioned and when it passes that test it shuts down.

After looking up my situation I came across 'Boot repair disk' which I burnt to a USB and ran in EFI mode, except when I get into it and try to run the boot rpair it says I must be connected the the internet, and I am, I know I am because the browser in the boot repair disk works and it says I'm connected... Here is the pastebin that the boot repair disk made with all the info it gathered I guess [http://paste.ubuntu.com/25990934/](http://paste.ubuntu.com/25990934/)

I'm pretty frustrated at this stage and don't know what else to do... The command I entered in windows earlier that seemed to break everything can be undone with this command ```
bcdedit /deletevalue {bootmgr} path \EFI\ubuntu\grubx64.efi
``` according the the article author but I have no way of getting into windows cmd to enter it.

Also I know windows is still there because I can see the windows disk and all its files in ubuntu.

Does anyone have any suggestions? They'd be greatly appreciated.

---

### Post by cmcanulty on 2017-11-19
After you set it to boot to hard drive did you save changes and exit? In most bios you hit F10 to save changes.

---

### Post by bennk on 2017-11-19
HI cmcanulty, thanks for the reply.

Yes, I saved all the changes

---

### Post by yancek on 2017-11-19
The first command you posted above using bcdedit would simply create an Ubuntu boot entry in the UEFI boot menu for Ubuntu.  The reason this did not work is because you did not install Ubuntu UEFI but rather the older MBR method.  Look at the entries at the top of the boot repair output for sda2 and you will see all the entries are for windows only.

The second bcdedit command you posted will accomplish nothing as all it would do is delete an entry in the UEFI menu for Ubuntu.  Since none exists, there is nothing to do.

Doing a dual boot install with windows 10 and Ubuntu using UEFI is explained at the official site below.  I would suggest reading that and possible re-installing Ubuntu and making sure it is booting UEFI and installing UEFI.  You may be able to repair it, the suggested repair indicates it will install Ubuntu EFI files.  I don't know why you are getting the error about internet connection.

You might wait for someone else more familiar with EFI to respond before doing a re-install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-11-19
You can use Boot-Repair and its advanced options to totally uninstall grub-pc (BIOS) and install grub-efi-amd64(UEFI) that will convert your install from BIOS boot to UEFI boot without total reinstall. Be sure to boot Ubuntu live installer in UEFI mode. 
It does look like Boot-Repair recognized you booted it in UEFI mode and was suggesting the grub-efi-amd64.
You can totally reinstall if you prefer, just only use Something Else and select existing partitions for new install.
You show a /boot partition. Most desktop installs do not require that. Full drive LVM or encrypted installs may need a /boot.

You will have old BIOS boot grub in MBR, it is space otherwise not used, but can be dangerous to delete with dd, so we leave it. But just never use BIOS/CSM/Legacy boot or it will try to use that old grub in gpt drive's protective MBR.

With UEFI system you want to always boot in UEFI mode. But when you boot flash drive, you have to select how you want to boot it each time.
And in UEFI you have settings to turn on/off UEFI, UEFI Secure Boot, and CSM/Legacy/BIOS, and that is for internal drive.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

UEFI has boot menu, often f10 or f12 check your manual. That should directly boot Windows.

What brand/model system?
What video card/chip?

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bennk on 2017-11-19
> **oldfred said:**
> You can use Boot-Repair and its advanced options to totally uninstall grub-pc (BIOS) and install grub-efi-amd64(UEFI) that will convert your install from BIOS boot to UEFI boot without total reinstall. Be sure to boot Ubuntu live installer in UEFI mode. 
It does look like Boot-Repair recognized you booted it in UEFI mode and was suggesting the grub-efi-amd64.
You can totally reinstall if you prefer, just only use Something Else and select existing partitions for new install.
You show a /boot partition. Most desktop installs do not require that. Full drive LVM or encrypted installs may need a /boot.

You will have old BIOS boot grub in MBR, it is space otherwise not used, but can be dangerous to delete with dd, so we leave it. But just never use BIOS/CSM/Legacy boot or it will try to use that old grub in gpt drive's protective MBR.

With UEFI system you want to always boot in UEFI mode. But when you boot flash drive, you have to select how you want to boot it each time.
And in UEFI you have settings to turn on/off UEFI, UEFI Secure Boot, and CSM/Legacy/BIOS, and that is for internal drive.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

UEFI has boot menu, often f10 or f12 check your manual. That should directly boot Windows.

What brand/model system?
What video card/chip?

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Its a dell Inspiron 15 laptop. Even if I reinstall ubuntu, how will that help with getting back into my windows?

---

### Post by oldfred on 2017-11-19
Can you not directly boot Windows from UEFI?

Dell seems to be the only one that requires CSM on but still select UEFI to boot. Most when CSM is on only boot in CSM/legacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Dell also requires you to change to AHCI mode for drive, to install Ubuntu as drive is set for RAID even when only one drive.
But Windows does not have the AHCI driver. If you did not install the AHCI driver before changing drive setting in UEFI, you can temporarily change it back, boot into Windows and add driver.
You may be able to boot in recovery mode, but directly booting from UEFI, but using f8 to get into repair/recovery console.
Did you make a Windows repair disk? Best to always have a flash drive with Windows recovery mode or Ubuntu's live installer available to make repairs.

      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[URL="https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en"]https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en
[/URL]
 Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch) mega-thread
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 

[URL="https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en"]
[/URL]

---

