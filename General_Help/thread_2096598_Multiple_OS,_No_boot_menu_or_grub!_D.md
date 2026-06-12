---
title: "Multiple OS, No boot menu or grub! D:"
date: 2012-12-20
forum: General Help
---

### Post by BlastDV on 2012-12-20
Hi everyone! I'm openning this new thread cause I think is a very specific situation am In.

Yesterday I just installed Ubuntu 12.04, Windows 7 and Windows XP in the same hard drive. As I expected, there was no menu at booting to choose the OS to start with, since this is not new for me, I just applied the common solution for this, so I used the following commands:

sudo fdisk -l
sudo mount /dev/sdaX /mnt (where X is the Ubuntu Installation Partition)
sudo grub-install –-root-directory=/mnt/ /dev/sda

This used to solve the problem! But yesterday it didn't, I also tried:

sudo mount /dev/sdaX /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
grub-install --recheck /dev/sda

And it was the same! When I turn on the PC, Ubuntu starts directly D=

Does anyone have an idea? Thanks!

---

### Post by oldfred on 2012-12-20
Maybe just
```
sudo update-grub
```If not run this:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemic")

---

### Post by BlastDV on 2012-12-20
This is the link I got:

[http://paste.ubuntu.com/1453958/](http://paste.ubuntu.com/1453958/)

I just used sudo update-grub and the boot menu appeared, but it only shows Ubuntu + (Recovery, memory test....) and Windows 7, if I choose Ubuntu everything goes fine, but when I tried to start Windows 7 then Windows XP is started instead! I thing the loader of XP overwrote the 7's so the grub.cfg specifies 7 to be in there but the actual loader is the XP's.

I tried to add a custom menu entry following some tutorials and if I use the sda1 where 7 is installed it stills loading XP, besides, if I use sda6, trying to boot my custom XP entry fails reporting and error with the MBR!

---

### Post by dnukumamras on 2012-12-20
Check out this link:

[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

it should work!! :D

---

### Post by oldfred on 2012-12-21
Windows only installs its boot files to the active partition. The active partition is the one in Linux shown with the boot flag. So both sets of boot files are in sda1. Not even sure where you installed your second Windows. Always best to install in primary partitions as you cannot delete sda1 as you need it to boot your other install.
```
sda1: ____________________________________

    File system:       ntfs
    [COLOR=DarkRed]Boot sector type:  Windows XP: NTFS[/COLOR]
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM
```       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

If sda1 is Windows 7 you may need to run repairs. In the Boot Sector is information on which boot loader to use ntldr for XP or bootmgr for Windows 7. It looks like you have the XP version so it will boot with XP.

I do not even know if you can add a Windows 7 entry to boot.ini. But With Windows 7 you may have to use bcdEdit to add the XP entry to allow booting both.

 How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

How Windows multi-Boots. Long explanation if you want details, but pictures give quick overview.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by dave.biagioni on 2012-12-22
Just wanted to report my experience with a nearly identical setup (including lack of boot menu).

I, too, installed Ubuntu (12.04) after Windows 7.  While  I could select the OS from within the BIOS menu, there was no Grub-type boot menu.

However, upon running boot-repair everything started working as expected.  I noticed that, by default, the program puts the boot files at the beginning of the drive (first partition, where some Windows files already sit), which perhaps is not the case when you are just installing Ubuntu from a disk or USB (?).  

The one issue I had is that at one point Windows performed a disk scan and figured out that its own boot files had been modified (I think?).  I don't have a screen shot to reproduce that portion, unfortunately.  Still, whatever it did had no effect on either installation and the boot menu still works correctly (for now!).

---

### Post by YannBuntu on 2012-12-22
> **oldfred said:**
> [https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

"Remic" --> "Remix"  ;)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by BlastDV on 2012-12-22
Hi there!

Reading the referenced article by oldfred, I could find out what went wrong.

I hope this next lines helps everyone with the same problem:

Windows tends to assume that it will be the only OS available in the machine it has been installed on, or at least, there may be other Windows Versions too, in the worst. Now, if you want to install two different versions of Windows on the same machine, you'll need to install older versions first, so that the booting system of the newest version can detect the older ones and put them all together in a single Boot Menu. If not, the older's will overwrite the "booting conf" with their own, which are not prepared to detect newer versions.

Having this clear, is also good to know that Windows doesn't work well booting over a Extended Partition (Ubuntu does), and my XP was there! So I think it just looked for a Primary NTFS partition to put its booting files, and in my case, the first one was the 7's. You can figure out what was the problem here ;)

Finally I just reinstalled everything but in the right order after figuring this; moved Swapping and Alpha Data partitions to an Extended Partition and XP, 7 and Ubuntu to Primary ones. The right order was:

Ubuntu
Windows XP
Windows 7

After that I just reinstalled the grub and updated it with a Live CD and that was all! :)

Now I get Ubuntu (recovery, memory testing...) and Windows 7 to boot with, and by selecting the 7's I get to a second boot menu offering "Older Windows Versions" and Windows 7 (this last menu was automatically generated by 7 by installing it after XP :D).

Thank's for your responses

---

### Post by oldfred on 2012-12-22
If both Windows are in primary partitions, you can move correct boot files back, change boot flag for each one and run repairs. Windows will only run repairs on boot partition or active partition. But then you can directly boot either install from grub. But if you install grub you would have to change Windows around again.

       A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

