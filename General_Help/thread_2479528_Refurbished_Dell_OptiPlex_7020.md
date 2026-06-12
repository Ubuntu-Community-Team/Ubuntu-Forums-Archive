---
title: "Refurbished Dell OptiPlex 7020"
date: 2022-09-28
forum: General Help
---

### Post by billywyatt2 on 2022-09-28
Being a silver surfer trying to save some money i decided to visit Amazon and purchase a refurbished desktop computer. I ended up buying a Dell OptiPlex 7020, which came with an 18/9" screen, keyboard and mouse plus two power cables and DVI cable. Which i think had Windows 11 pro pre-installed. All for £250! 

I did intend to set up the machine, download and install Ubuntu 22.04.1 and delete the unwanted Windows OS. 
The problem is after setting up the machine the Dell logo appears and then an Auto config please wait and finally
Input not supported.

Have tried setting up the machine with new cables, keyboard and mouse but when i try and boot up the machine
all i ever get is Input not supported.

Could someone help me please.

---

### Post by ActionParsnip on 2022-09-28
[https://www.dell.com/community/Optiplex-Desktops/Dell-OptiPlex-7020-display-problem/td-p/8051652](https://www.dell.com/community/Optiplex-Desktops/Dell-OptiPlex-7020-display-problem/td-p/8051652)

Have you tried a different display?

---

### Post by oldfred on 2022-09-28
Windows 11 would not work on that machine.  Needs 8th Gen Intel chips or later. It may install, but is not update-able. 
I have similar Dell Inspiron 3647 with i3-4160 (4th Gen).

Do not remember any issues installing in UEFI boot mode as dual boot with Windows. 
System primarily used with TV so needed Windows as Comcast/Xfinity would not work with Ubuntu. 
Have not reinstalled Ubuntu lately. Its in Fl at Condo & if Hurricane does not destroy it, will update it end of Oct. when I get there.

Not sure what UEFI settings I now changed, but I did update UEFI to latest available from Dell at the time. Did not keep list on Dell, but my Asus motherboard needed 7 settings in UEFI changed. Some required & some just to have it work better.

If Windows still installed, it may have fast start up on which locks the NTFS partitions in read only mode.
Drives normally need AHCI setting, and back then Dell used  RAID or Intel RST.
Fast Boot in UEFI needs to be off. That assumes no system changes are made. 

UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)
[https://ubuntuforums.org/showthread.php?t=2461231](https://ubuntuforums.org/showthread.php?t=2461231)

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

