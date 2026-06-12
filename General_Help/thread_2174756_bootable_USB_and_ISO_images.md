---
title: "bootable USB and ISO images"
date: 2013-09-16
forum: General Help
---

### Post by proton1h1 on 2013-09-16
[TABLE]
[TR]
[TD="class: votecell"]

              [/TD]
              [TD="class: postcell"]                I've some question regarding bootable pendrive and ISO.
  
[LIST]
[*]How to make a normal ISOimage(just containing folders) or USB  boot-able ,if one wants to do it manually, how to do it ?
[*]what is difference in BOOTSECTOR of normal pendrive and a bootable pendrive ?
[*]What if I have UBUNTU ISO(not a LIVE-CD) with all it's content, how to  make it bootable?
[/LIST]
  Any help or link will work too ...... 
      

[/TD]
[/TR]
[/TABLE]

---

### Post by sudodus on 2013-09-16
Welcome to the Ubuntu Forums :-)

You can start looking at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

and come back with more questions afterwards

---

### Post by proton1h1 on 2013-10-02
thank you sir ...!! 
dd method didn't worked for me ...!
I used this command...
**dd if=/media/impStuff/diskImages/image.iso of=/dev/sdb1 bs=4096**
For the same image, when i use **'unetbootin**' it works ...you
I saw installing grub method in pendrive, that seems little tedious and is not properly explained ....
Using **dd** or **installingGrub** any of these methods are nice to understand things....
But till now, I've always used **unetbootin** to make bootable pendrive....and it has always worked for me, but now I want to understand that, before i use software to ease my work ....
2. Sir, i used to use win7 earlier and used to follow these steps: 
    LIST DISK
    Selecting my DISK
    CLEAN 
    CREATE PARTITION PRIMARY
    SELECT PARITITION 1
    ACTIVE    //when i used help for it: It says, this command makes the disk ACTIVE
    FORMAT FS=FAT32
    ASSIGN
    ACTIVE

and then move the contents to Disk drive, just copy pasting and it used to work for me too. If you know it, please tell me how did this work ....!!

---

### Post by sudodus on 2013-10-02
> **proton1h1 said:**
> thank you sir ...!! 
dd method didn't worked for me ...!
I used this command...
**dd if=/media/impStuff/diskImages/image.iso of=/dev/sdb1 bs=4096**

You had the wrong target. You cloned the iso file to the first partition, when you should have cloned it to the whole drive /dev/sdb

```
dd if=/media/impStuff/diskImages/image.iso [COLOR=#ff0000]of=/dev/sdb[/COLOR] bs=4096
```
> 
For the same image, when i use **'unetbootin**' it works ...you
I saw installing grub method in pendrive, that seems little tedious and is not properly explained ....
Using **dd** or **installingGrub** any of these methods are nice to understand things....
But till now, I've always used **unetbootin** to make bootable pendrive....and it has always worked for me, but now I want to understand that, before i use software to ease my work ....

I'm glad ***unetbootin*** works well for you :-)
> 
2. Sir, i used to use win7 earlier and used to follow these steps: 
    LIST DISK
    Selecting my DISK
    CLEAN 
    CREATE PARTITION PRIMARY
    SELECT PARITITION 1
    ACTIVE    //when i used help for it: It says, this command makes the disk ACTIVE
    FORMAT FS=FAT32
    ASSIGN
    ACTIVE

and then move the contents to Disk drive, just copy pasting and it used to work for me too. If you know it, please tell me how did this work ....!!
I use Windows very seldom nowadays ...

- ***Clean*** might mean that you delete the partition table.
- ***Active*** probably means that you add that boot flag for the partition. It is used by Windows, but not necessary for Linux.
- Making*** partitions and file systems*** is quite easy to do with ***gparted*** from a live USB CD/DVD/USB drive. Unetbootin needs it, but if you clone with ***dd***, it is not necessary, the cloning will create 'everything' in one single step.

---

### Post by oldfred on 2013-10-02
Only some ISO can use dd as they have to be configured that way.

 The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. Or you can use dd.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

The standard ISO on a flash drive uses syslinux boot loader which works like Windows boot loader. It has code in MBR and more code in PBR - partition boot sector. Configuration files are then in install's isolinux folders. 
New versions use grub for UEFI boot, so it also has grub in efi partition and grub2's efi files in /boot.
Grub with BIOS boot has code in MBR, but does not use PBR.

This shows Vista, but is how BIOS/MBR systems boot with MBR & PBR.
      
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by proton1h1 on 2013-10-12
finally "dd" worked with hybrid iso, and it's the easiest method. Meanwhile i found "syslinux", syslinux method was better for me, since i can use the pendrive after making it bootable to store my data too. All my doubts about bootable part in the disc are clear too, and remaining will go out by time ..!! :) :):):)
Thanks for help    [**[COLOR=#000000]sudodus [/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021")and [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")

---

