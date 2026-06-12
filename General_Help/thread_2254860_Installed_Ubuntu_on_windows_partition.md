---
title: "Installed Ubuntu on windows partition?"
date: 2014-11-30
forum: General Help
---

### Post by nick159 on 2014-11-30
I have been attempting to install Ubuntu on Windows 8. I created a partition and when I went to install I selected the partition and created a root. I think I forgot to select the partition and I hit install. After the install I restarted my laptop. It messed up my pc, windows recovery booted and I recovered all my info. When I went back to try again, the options said install Ubuntu 12.04 LTS alongside Ubuntu 12.04 LTS. So it must still be on my harddrive. I think I may have installed them on the same partition. How can I fix this problem and dual boot Windows 8 and Ubuntu.

---

### Post by Bashing-om on 2014-11-30
nick159; Hello;

Presently, are you able to boot Windows ?

Upfront, I am not familiar with Win8 -> UEFI -> GPT partitioning. However, I can advise what information to provide to enable those who do know.
Boot the liveDVD of ubuntu to terminal, post back - Between Code Tags - the outputs of terminal commands:
```

sudo parted -l
sudo parted /dev/sda unit s print
sudo blkid -c /dev/null

```

Which will show the partitioning of the hard disk(s), and as well point to the location of the 'EFI' boot files. Then we can look and know how you are booting ; secure boot , EFI, legacy (??) .

[INDENT]the longest journey begins with
[INDENT][INDENT][INDENT]that first step[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nick159 on 2014-11-30
parted: invalid option -- '1'
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start       End         Size        File system     Name                          Flags
 1      2048s       821247s     819200s     ntfs            Basic data partition          hidden, diag
 2      821248s     1353727s    532480s     fat32           EFI system partition          boot
 3      1353728s    1615871s    262144s                     Microsoft reserved partition  msftres
 4      1615872s    622604287s  620988416s  ntfs            Basic data partition          msftdata
 7      622604288s  626604031s  3999744s    linux-swap(v1)
 8      626604032s  929804287s  303200256s  ext4
 5      929804288s  930725887s  921600s     ntfs                                          hidden, diag
 6      930725888s  976773119s  46047232s   ntfs            Basic data partition          hidden, msftdata


/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WINRE" UUID="F628A7BA28A7786F" TYPE="ntfs" 
/dev/sda2: UUID="A4B3-6439" TYPE="vfat" 
/dev/sda4: LABEL="Windows" UUID="12FEEEA5FEEE8079" TYPE="ntfs" 
/dev/sda5: UUID="3AAAB4C4AAB47DC7" TYPE="ntfs" 
/dev/sda6: LABEL="RECOVERY" UUID="8840A1E040A1D56A" TYPE="ntfs" 
/dev/sda7: UUID="8a690343-fb91-4552-9712-9545ff2a2d36" TYPE="swap" 
/dev/sda8: UUID="369cf441-6ccd-464a-b8cf-00f29c3c9928" TYPE="ext4" 
/dev/sdb1: LABEL="UUI" UUID="E4FE-FA3D" TYPE="vfat" 

Not sure if I did that right, but that is what it said after the codes.

---

### Post by Bashing-om on 2014-11-30
nick159; Hey;

You are doing well. So far, so good.
Code tags, please; Makes the outputs so much more the readable.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The command " sudo parted -l " where the argument to the command is a lower case "L" rather than a '1' .

OK, we know that ubuntu is installed to partition 'sda8' and the boot files are located in 'sda2' ; and the good news - all partitions are recognized.

Now it is but a matter of of making sure that you are booting in EFI mode, and that the proper files are installed in that boot partition. The thing now is that I do not have the experience to determine what files are required. Others will have to pick up at this point.

Again, are you able to boot Windows ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by nick159 on 2014-11-30
Yes, windows loads up automatically. I do not get the screen on boot to pick ubuntu or windows.

---

### Post by Bashing-om on 2014-11-30
nick159; Great ;

Maybe, just maybe it is but a matter of telling the firmware what to boot with a function key -> boot menu ?

As advised, I do not have the experience to advise further, those who do will respond.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by nick159 on 2014-11-30
I dont know if this matters, but I tried moving OS Boot Manager up in the BIOS, when I rebooted it just loaded Windows 8.

---

### Post by oldfred on 2014-11-30
What brand/model computer and what video card.

May be best to see details, post link to summary report. 
Do not run auto fix until someone has reviewed report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nick159 on 2014-11-30
384MB ATI AMD Radeon HD 6310 Graphics

[h=1][SIZE=4]HP 2000-2d09WM Notebook[/SIZE][/h]

---

### Post by oldfred on 2014-11-30
Have not seen anyone else with that specific model, but all HP have issues. They have modified UEFI to only boot Windows, so work arounds are required.

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

Some of the various work arounds, best to see details but most seem to rename bootx64.efi.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

