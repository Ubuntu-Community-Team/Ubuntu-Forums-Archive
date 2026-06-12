---
title: "Ubuntu Windows 10 Dual Boot Boot-repair is not working"
date: 2022-04-24
forum: General Help
---

### Post by bloombloom on 2022-04-24
I have a dell xps 15 with windows 10-ubuntu 16.04 lts dual boot on an SSD  hard drive. Somehow, windows got stuck in the automatic repair page and I lost the grub lootloader. Normally, this would have been fixed by boot-repair-disk on a live usb but boot-repair does not recommend any repairs. I managed to add efi file and get the grub screen but none of the operating systems are currently working. I restored bios settings: I then disabled legacy roms and secure boot. 

I haven't switched from RAID on to AHCI. 

I am not sure what is going on or what are the next steps, any help is appreciated. Adding the boot-info paste bin here:
[https://paste.ubuntu.com/p/6dGfCnKDzT/](https://paste.ubuntu.com/p/6dGfCnKDzT/)

---

### Post by yancek on 2022-04-24
Support for a standard 16.04 install ended a year ago.  If you have solid backups, it might be best to install a newer LTS version.

I don't know what the problem is but if you look at the boot repair output, there is no information on your hard drive(s) only on the USB with boot repair.  This is often indicative of a hardware failure.  Boot repair does show entries in EFI for both windows and Ubuntu.  Have you tried booting by accessing the BIOS firmware and selecting either the windows or ubuntu options?

Have you been successfully booting both windows and Ubuntu for some time?  If so, were any changes made to the system shortly before this problem occurred?
You might try setting AHCI in the BIOS.

---

### Post by oldfred on 2022-04-24
Ubuntu/Boot-Repair will not see drives in Intel RST/Optane. You need to change to AHCI. And then install AHCI drivers into Windows or Windows will not boot.
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735) & 
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)
DEll app
removal (setuprst.exe and setupoptanememory.exe - both from Dell

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Dell XPS 15
[https://askubuntu.com/questions/1042414/trying-to-install-ubuntu-on-dell-xps-15-9570](https://askubuntu.com/questions/1042414/trying-to-install-ubuntu-on-dell-xps-15-9570) & 
[https://askubuntu.com/questions/1046263/dell-xps-15-9570-2018-disable-nvidia-gpu](https://askubuntu.com/questions/1046263/dell-xps-15-9570-2018-disable-nvidia-gpu)
[https://ubuntuforums.org/showthread.php?t=2413124](https://ubuntuforums.org/showthread.php?t=2413124)

---

### Post by bloombloom on 2022-04-24
Thank you for your suggestions. Switching from RAID on to AHCI then running boot-repair again solved my boot issues and I could access both partitions. Here's the new pastebin for the record:
[https://pastebin.ubuntu.com/p/fPfyP5CSX8/](https://pastebin.ubuntu.com/p/fPfyP5CSX8/)

---

