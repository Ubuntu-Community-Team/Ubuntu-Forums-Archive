---
title: "Installing BURG"
date: 2014-12-23
forum: General Help
---

### Post by GARoss on 2014-12-23
I would like to install BURG.  In the process of install I've hit a snag I wont go further until I'm sure which to select.  

I have 4 hard drives on my computer.  One drive, not Windows C: but a large storage drive, was partitioned for Ubuntu 14.04 @ 19Gb + 2Gb Swap.  In "Configuring burg-pc" photo below, is this where "Package configuration" is asking for GRUB install devices?  How to make sure which is correct - /dev/sda, b, c or d?

[ATTACH=CONFIG]258752[/ATTACH]

---

### Post by GARoss on 2014-12-23
I believe /dev/sda would be correct but just want assurance.  The 128Gb drive is also Windows C: .  Thanks.

**This is what the terminal says**.  

[I]george@george-P67A-UD3-B3:~$ sudo fdisk -l
[sudo] password for george: 

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfb2ef09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   250066943   124930048    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f757a46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2889312255  1444655104    7  HPFS/NTFS/exFAT
/dev/sdb2      2889312256  2926370815    18529280   83  Linux
/dev/sdb3      2926372862  2930276351     1951745    5  Extended
/dev/sdb5      2926372864  2930276351     1951744   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6924b373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeff171b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT
george@george-P67A-UD3-B3:~$[/I]

---

### Post by nerdtron on 2014-12-23
Linux is installed on /dev/sdb drive.

You want to replace GRUB with BURG? Then what drive did you installed GRUB during the installation?

---

### Post by DuckHook on 2014-12-23
BURG has been unsupported for years. Not at all recommended. Stick with GRUB. If you run into trouble with BURG, there are now very few people who can help you.

---

### Post by GARoss on 2014-12-23
> **nerdtron said:**
> Linux is installed on /dev/sdb drive.

You want to replace GRUB with BURG? Then what drive did you installed GRUB during the installation?

Just confused when I got to this point of the install...

[ATTACH=CONFIG]258759[/ATTACH]

... & didn't want to mess up.  Need to be sure.

Ubuntu is installed on Disk 2 (/dev/sdb2), 17.67Gb.  Swap is 1.86Gb.  Would /dev/sdb be correct?  As you pointed out, that is where Ubuntu is installed.  BTW - I did extensive searches before posting & could only find a tutorial for a single drive install of Burg, not multiple drives like mine.  
 
[ATTACH=CONFIG]258758[/ATTACH]

[I]Device Boot Start End Blocks Id System
/dev/sdb1 2048 2889312255 1444655104 7 HPFS/NTFS/exFAT
**/dev/sdb2 2889312256 2926370815 18529280 83 Linux**
/dev/sdb3 2926372862 2930276351 1951745 5 Extended
/dev/sdb5 2926372864 2930276351 1951744 82 Linux swap / Solaris[/I]

---

### Post by GARoss on 2014-12-23
> **DuckHook said:**
> BURG has been unsupported for years. Not at all recommended. Stick with GRUB. If you run into trouble with BURG, there are now very few people who can help you.

Thanks.  My main goal to to enlarge the text but thought BURG might be ok.  I don't understand how to edit GRUB or GRUB 2.

---

### Post by oldfred on 2014-12-23
If you just want larger fonts, there may be two ways. 
One is that you do not have correct video mode. 
The other is edit grub. Links show colors, fonts and various other settings.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by GARoss on 2014-12-24
Got it!  Thanks

---

