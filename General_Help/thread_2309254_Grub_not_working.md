---
title: "Grub not working"
date: 2016-01-09
forum: General Help
---

### Post by UngusOptonline.ne on 2016-01-09
Hello all, I've been using Ubuntu for a few yrs and have usually been able to fix any problems using search engines and past posts but this one has me stumped.

I have been running Ubuntu 14.04 with the latest update AND Win8.1 in dual boot since Win8 came out and was doing so with Win7 as well. Today for some unknown reason the grub stopped working. At first I was getting the >grub prompt and using 'ls' I found the partition hd0,msdos1 but could not find any module files or usr/lib.

I was able to use the setup menu to boot into windows. However, The Ubuntu option in setup placed me back to the >grub prompt.

I made an iso to usb image of Boot Repair and booted into it. Followed the directions, and BR said it was fixed. Rebooted and it went straight to Windows Boot Manager with Win8 as the only option.

I then used the latest Ubuntu install from a USB and entered as a trial use. Went to the Terminal and tried boot repair from there. This did not wrk either. My error number is  [http://paste.ubuntu.com/14444499/](http://paste.ubuntu.com/14444499/)  

hd0,msdos1 no longer exists when I run ls at the >grub prompt. I was able to find a backup MBR file on hd0,gpt2 but I have no idea how to use it.

I have a Toshiba Satellite C55A using Ubuntu 14.04 and Win 8, UEFI is on, Secureboot is off.

Any help much appreciated

---

### Post by yancek on 2016-01-09
The reason Ubuntu doesn't boot is because it isn't installed.  Not sure what you did but the only sign of any Linux system is on the flash drive and the EFI partition of your hard drive so obviously it had been installed at some point.  What updates/changes did you make immediately prior to having this problem?  You also have windows code in the MBR of both your drives as well as an EFI partition.  They are incompatible, need to be only EFI or only MBR.

---

### Post by Dennis N on 2016-01-09
...and no partitions with ext4 filesystems. Did you reformat any? Examining /EFI/ubuntu/grub.cfg on the EFI system partition should reveal where Ubuntu was. 

```
dmn@Zotac:/boot/efi/EFI/ubuntu$ cat grub.cfg
search.fs_uuid 03e8df34-860c-49b5-ab5a-33cc60bb7215 root [COLOR="#FF0000"]hd0,gpt2[/COLOR] 

```

---

### Post by UngusOptonline.ne on 2016-01-11
The partion dedicated to Ubuntu shows 3GB of space used when I look in Windows disk manager, so I'm assuming the OS and Data are still there.

All I did was awake the computer from sleep and it froze. I had to to a soft reset (power button held for 7 seconds) That is when the Grub stopped working as described.

Sorry for the delay in responding. Busy with work. All help much appreciated.

---

### Post by LostFarmer on 2016-01-11
```
/dev/sda6   1,935,955,968 1,953,523,711    17,567,744 Windows Recovery Environment (Windows)

```  That read out is wrong.  Not only is the start sector outside of disk but the ending sector is before the start sector.  This is the 2nd time I have seen this error from 'boot repair'.

we need a correct readout of the hdd partitions.  From a linux live terminal run and post output of :
```
sudo parted -l
```   Note: -l is a small L

---

### Post by UngusOptonline.ne on 2016-01-11
On hd0,gpt2 I have /boot-sav , /efi , / bootsect.bak System Volume Infomation

ls /boot-sav gives me a response of / log , and / mbr_backups/    

ls / efi gives me a response of / Microsoft , / Boot , / Toshiba , / ubuntu

ls / ubuntu gives me / shimx64.efi grubx64.efi Mokmanager.efi grub.cfg bootx64.efi   (note there are no / between the different files)

OK, I'll pick this up tmrw and post the results from the sudo parted cmd.

Thanks everyone for their patience.

---

### Post by UngusOptonline.ne on 2016-01-21
Sorry for the delay in responding....

I booted into Ubuntu trial mode and ran sudo parted -l and these are the results:

~Model: ATA ST1000LM024 HN-M (scsi) 
Disk /dev/sda: 1000GB 
Sector size (logical/physical):512B/4096B 
Partition Table: gpt 


Number  Start   End     Size    Filesystem  Name                  Flags 
 1      1049kB  1075MB  1074MB  ntfs        Basic data partition  hidden, diag 
 2      1075MB  1180MB  105MB   fat32       Basic data partition  boot 
 3      1180MB  1314MB  134MB   ntfs        Basic data partition  msftres 
 4      1314MB  677GB   675GB   ntfs        Basic data partition  msftdata 
 5      677GB   991GB   315GB   ntfs        Basic data partition  msftdata 
 6      991GB   1000GB  8995MB  ntfs        Basic data partition  hidden, diag 




Model: PNY USB 2.0 FD (scsi) 
Disk /dev/sdb: 8167MB 
Sector size (logical/physical):512B/512B 
Partition Table: msdos 


Number  Start             End                        Size              Type        File       system      Flags 
 1         1049kB    8166MB         8165MB      primary              fat32                 boot

---

### Post by Vladlenin5000 on 2016-01-21
Clearly posts #2 and #3 are correct.

---

### Post by LostFarmer on 2016-01-21
The output does not show any linux partitions.    Your old pastbin does indicate that ubuntu was installed.  So not sure yet what is the problem, only more questions.
!) might you have a 2nd internal hdd that is not working where linux was installed ?
2)boot into the live ubuntu and try to mount and look in all the listed partitions.  Do they mount ?  is yes, are they all MS Window partitions as 'parted ' says they are ? (If you do not know how via a terminal to mount, try program 'disk').

3) Go to the 'EFI' partition (sda2) and open 'grub.cfg) in /efi/ubuntu/  .  The first line will give the location where linux was.

If we can determine if one of the NTFS reported partitions is in fact a linux partition , you MIGHT be abe to change the partiton type, but do not count on it.

> ls /boot-sav gives me a response of / log 
in /boot-sav/log/"date"/sdX/current_mbr.img is a copy of the partition table but if it is after the problem then it would also have the problems.

---

### Post by UngusOptonline.ne on 2016-01-24
No second HDD. Am I better off formatting the SDA2 diskspace (:U drive in Windows) and reinstalling Ubuntu? Most of my docs and pics are backed up on Google drive with InSync.

---

### Post by yancek on 2016-01-24
> Am I better off formatting the SDA2 diskspace

No.  You won't be able to boot anything if you do that because it is your EFI partition with the EFI boot files and is only 105MB.  It looks like sda4 is your windows system partition, not sure what the other partitions are.  Maybe sda5 is where you had Ubuntu, 315GB partition?  You might try mounting it and looking at the files.  You could shrink one of the partitions and create another for Ubuntu.  You still have the problem of having an EFI partition and windows code in the MBR of the drive.  Those two are not compatible.  I don't use UEFI myself so you will need to wait for someone else to come along to suggest a method to repair this problem.  If you are using GPT partitioning, I believe you need to use EFI for windows.

---

### Post by oldfred on 2016-01-24
Generally once a boot loader is loaded to the MBR even with gpt, we do not try to erase it. Using dd to erase things is more dangerous than just leaving it.
But you must never set system to boot in Legacy/BIOS/CSM boot mode. Only ever boot in UEFI boot mode. If you try to boot in BIOS mode it will try to use code in MBR which will never work.

---

### Post by UngusOptonline.ne on 2016-01-24
Yes, SDA5 is the Ubuntu partition. How can I mount it? Do I use the Trial mode or do I create another partition and install Ubuntu there and then attempt to mount and read the SDA5 partition?

---

### Post by oldfred on 2016-01-25
You always should be able to boot live installer in live mode.
UEFI gives two ways to boot live installer. UEFI:name and name where just the name/label of flash drive is the BIOS boot.
You should be able to choose from UEFI boot menu or one time boot key. One time boot key is often f10 or f12, but varies my brand, check your manual.
If UEFI and you left fast start in UEFI on, you may have trouble getting into UEFI. Fast start in UEFI is another Windows requirement. It assumes no hardware changes and skips all the checks for new/changed hardware. That means it boots fast, but you do not have any or much time to press any key to get into UEFI or choose boot. Most will work from a full cold boot, or power down, remove battery if laptop, and hold power switch to totally drain system. Then immediately press correct key on boot up. Some have tiny reset pin hole on bottom of system. And some just require jumping pins on motherboard or removing coin battery on motherboard.

---

### Post by UngusOptonline.ne on 2016-02-06
When I boot up the computer I can press F2 and "enter setup" where choosing the HDD gives me TWO ubuntu boot options (which both work) and Windows. I reinstalled Ubuntu 14.04 and it looks like its a fresh install as it does not resemble my previous layout and my insync program is not there anymore.

I've tried boot repair several times from the Terminal but it hasn't worked. There is an efi.bak file in Windows that has many shimx and mokmgr and other .efi files.

So is there any hope in getting the GRUB to work or am I resigned to booting the above way?

---

### Post by Vladlenin5000 on 2016-02-06
Try ```
sudo update-grub
``` from your Ubuntu.

---

### Post by oldfred on 2016-02-07
Did you update UEFI/BIOS from Toshiba.
That is a good idea, but Toshiba now is like several other vendors and now uses description as part of boot. And only valid description is "Windows". Use of description is sepcifically NOT allowed per UEFI spec.

Work around is normally to copy /EFI/ubuntu into /EFI/Boot. Then backup bootx64.efi. If you have run fixes from Boot-Repair it may have done that.
And then rename shimx64.efi to bootx64.efi. And then use (or add if you do not have it) the EFI: hard drive entry to boot. You should be able to set that as default in UEFI, but major Windows updates will keep resetting Windows to first in boot order.

All of these links are essentially the same instructions as above. Some with Toshiba may have more details on other Toshiba issues.

       Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[URL="http://ubuntuforums.org/showthread.php?t=2267408"]http://ubuntuforums.org/showthread.php?t=2267408
      [/URL]
 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

Detail instructions also in link in my signature.

 [https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by UngusOptonline.ne on 2016-02-14
Where I am right now is I can still Dual-Boot by pressing ESC when the computer boots to a screen that gives me Win 8.1 as the only OS option. Pressing ESC brings me to a screen that gives me the option to boot from the HDD, USB, or CD. I choose HDD and it gives me the Windows option as well as two Ubuntu options (one "Ubuntu" and the other "ubuntu") Both boot into the same Ubuntu OS.

So I'll stay with this and if I ever get another laptop I'll use one for Win and one for Linux.

Thanks for your help everyone and I hope my experience and results are helpful to the community in some way.

---

