---
title: "Ubuntu on external drive"
date: 2013-01-14
forum: General Help
---

### Post by northwestern on 2013-01-14
Hi
I have a new Samsung series 3 laptop with Window 8 pre-installed, I have had mixed success with loading Ubuntu 12.10 from a USB flash pen onto a USB 3 external drive. The program loads OK but when I try to boot back into Windows 8 I get a screen saying GRUB 2 :press tab for further information (or something like that), I then have to factory reset my machine to get it going again.
On my old laptop using Windows 7 it was a simple job and I know that Windows 8 present difficulties. Before I just created EXT 4 & swap partition is are what I have been using in Windows 8.
Now however I am faced with more options, these are:
**EXT 4 Journaling file system.**
**EXT 3 Journaling file system.**
**EXT 2 file system.**
**ReiserFS Journaling file system.**
**JFS Journaling file sys.**
**XEXT 4 Journaling file system.**
**FS Journaling file system.**
**FAT 16 file system.**
**FAT 32 file system.**
**NTFS.**
**swap area.**
**EFI boot partition.**
Should I be using any of the above new options?
I am sorrow for the long message but I am determined to get Ubuntu to run from an external drive and any help would be appreciated.
Regards
Northwestern

---

### Post by oldfred on 2013-01-14
If you have Windows in UEFI mode, you already have an efi partition that grub will use. You only have to have / (root) probably ext4 and swap. You can create /home as ext4 and I do recommend a shared NTFS data partition when dual booting with Windows. If saving most data in the shared NTFS, you may not need separate /home, just make / a bit bigger. 

I use ext4 - 25GB for / including my /home and have a shared NTFS and a shared ext4 (both 100GB). No new data is going into my NTFS as I do not boot XP anymore but have several Ubuntu installs so I have a shared Linux data partition. I am aggressive about moving data to data partitions to keep /home only really having my user settings. But have not moved .wine so my /home is about 2GB of the 9GB I use.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
       Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by fantab on 2013-01-14
Disable UEFI in your bios, and you should be good. You can usually do this by choosing "Legacy Boot Mode" under the UEFI option.

I think you will have to DISABLE UEFI in your BIOS. It can be done by opting for "Legacy Boot Mode" or something similar in your options. I am not sure about this as I haven't yet tried to dual boot with "Secure Boot" Windows 8... you may want to wait for a more confirmed reply.

Good Luck..

Edit: oldfred beat me to it with a more comprehensive reply... follow the above post to the letter.

---

### Post by northwestern on 2013-01-14
Thank for your replies.
My external drive is 500gb, all of which I intend to use for Ubuntu, 494 gb /root EXT 4 & 6gb swap.
I am trying to load 12.10 which i'm led to believe loads in UEFI mode, where am I going wrong to corrupt the windows MBR , I always make sure that I put the Ubuntu boot loader on the external drive.
Regards
Northwestern.

---

### Post by oldfred on 2013-01-14
One of the advantages of UEFI is that now you have an efi partition and every install's boot loader goes into the efi partition. It is like having an unlimited number of MBR's and no issues of conflicts (this is if UEFI is working the way it is supposed to work).

---

### Post by northwestern on 2013-01-14
Thanks for your replyAlthough I found using an external drive on my old ( broken) Windows 7 laptop fairly simple I must confess that I am now having problems. After reading your excellent replies I have been trying to get my head round the problem loading Ubuntu 12.10, I seem to be going from one web page to another without success. Is there a website anywhere where that explains in simple terms how I can get over my problem (I am really missing Ubuntu).
I am sure that If i turn off my secure boot within the bios that my windows will not open.
Thanks for your patience.
Northwestern

---

### Post by oldfred on 2013-01-14
It is part of the Windows UEFI specification that the user be allowed to turn secure boot off. If it does not then the vendor did not comply with Microsoft specifications. (But some UEFI do have issues.)

---

### Post by northwestern on 2013-01-14
Thanks for your continued help.
When I go into BIOS and disable the secure boot another options box appears below giving me three options.
[B]UEFI OS
CSM OS
UEFI and Legacy OS[/B]

Which of these options should I choose ?
Regards
Northwestern

---

### Post by oldfred on 2013-01-14
UEFI OS. Unless this means secure boot on your system

CSM I believe is another name for BIOS or legacy. 

Not exactly sure what UEFI and legacy takes you to. Unless it means any system that is not secure boot.

---

