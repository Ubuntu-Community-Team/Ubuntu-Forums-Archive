---
title: "Windows 8.1 don't boot"
date: 2014-04-21
forum: General Help
---

### Post by stphane3 on 2014-04-21
Hi guys! 

After installing Ubuntu 14.04 (64bit), Windows 8.1 will not start. I tried several things: 

- Repair with boot-repair ([http://paste.ubuntu.com/7294572/](http://paste.ubuntu.com/7294572/)) 
- System Update of grump (sudo update-grub) 

I also tried a repair with the Windows disk, but Grump boot before, so not possible to start the CD: (

No results. I said that last year, after a crappy dual boot with Ubuntu 13, I have to press "enter" to boot my PC (black screen with white line flashing + A2 bottom right). I do not know if it is a problem or not, but I prefer to give smile 

My config: 

Processor: Intel Pentium DualCore H640 
Motherboard: MSI B75A-G43 
Graphics Card: NVIDIA GeForce GT 330 

Do you have any idea? Here is the report of boot-repair: [http://paste.ubuntu.com/7294572](http://paste.ubuntu.com/7294572) 

Thank you very much!

---

### Post by stphane3 on 2014-04-21
After more test, i would like start the Cd/dvd before grub or add this option. But no result at this time :(

---

### Post by den_ on 2014-04-21
> **stphane3 said:**
> Hi guys! 

After installing Ubuntu 14.04 (64bit), Windows 8.1 will not start. I tried several things: 

- Repair with boot-repair ([http://paste.ubuntu.com/7294572/](http://paste.ubuntu.com/7294572/)) 
- System Update of grump (sudo update-grub) 

I also tried a repair with the Windows disk, but Grump boot before, so not possible to start the CD: (

No results. I said that last year, after a crappy dual boot with Ubuntu 13, I have to press "enter" to boot my PC (black screen with white line flashing + A2 bottom right). I do not know if it is a problem or not, but I prefer to give smile 

My config: 

Processor: Intel Pentium DualCore H640 
Motherboard: MSI B75A-G43 
Graphics Card: NVIDIA GeForce GT 330 

Do you have any idea? Here is the report of boot-repair: [http://paste.ubuntu.com/7294572](http://paste.ubuntu.com/7294572) 

Thank you very much!
You have issues with disks, but you mention you Grpahics. You have one, two , or which number of disks? Which kind of disks (SSD, SATA)? How did you install Ubuntu, have you manually repartitioned, or used one of more comfortable options. Output of 'sudo fdisk -l /dev/sda', 'sudo gdisk -l /dev/sda'. Same for sdb, sdc, according to the number of disks you have.

---

### Post by stphane3 on 2014-04-21
Hi Den,

Now i can boot the CD before grub. I've 5 HDD (1ssd with Windows and Ubuntu). The other HDD is for file stockage.

For the install, i've use a partition "not aloued" for Ubuntu.

---

### Post by nuttzo31 on 2014-04-21
You don't state how many disk or what your dual boot setup is but,

Try pressing delete or f2 constantly while computer boots, you should be able to get to your bios before grub boots.

If you have UEFI you may have an option for windows boot loader in the bios, if you do see if you can boot windows directly.

---

### Post by stphane3 on 2014-04-21
Hi,
 
My dualboot is on one disk (SSD). In the BIOS, I only UEFI "for no device detected"

---

### Post by stphane3 on 2014-04-21
I added attached a photo of my boot (f11) at startup. My two systems are in SATA1.

When grub starts, it does not propose to Windows 8.

[http://img11.hostingpics.net/pics/796130WP20140421002.jpg](http://img11.hostingpics.net/pics/796130WP20140421002.jpg)

---

### Post by oldfred on 2014-04-21
You cannot install grub to a NTFS PBR or partition boot sector.

>  sda1: _______________________________________
    File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 211280864 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe



But NTFS does keep a backup of the PBR, so you can use testdisk to restore from backup.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You also are not showing a BCD in your Windows. So your Windows may also need repairs from Windows repairCD or flash drive. But Windows repair will not even recognize your NTFS partition until you restore a NTFS PBR.

---

### Post by stphane3 on 2014-04-21
Hi Oldfred,

I'm not sure I understood it was the problem and what steps I should follow to solve it, sorry. 

Could you (re)explain me?

---

### Post by oldfred on 2014-04-21
Click on either of the methods posted, or actually review both as the are similar.
They show the detailed steps required.

You have to use testdisk to restore a NTFS partition boot sector PBR or BS as having grub installed to the PBR damages Windows.

You almost never install grub boot loader to a partition, and never install it to a NTFS partition. Grub2's boot loader must be in the MBR of a hard drive for BIOS boot (or efi partition for new UEFI systems) as that is how systems boot. Only if you have another Linux install with another version of grub may you install grub to a PBR.

The MBR is the very first sector of a hard drive like sda, sdb etc and BIOS looks there for boot code.
A PBR is the first sector of every partition like sda1, sda2, sdb1 etc, Windows uses that for more boot code.
Grub does not use PBR.

---

### Post by stphane3 on 2014-04-21
Thank you very much, my problem is solved! I followed the steps in your first link ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)) and it works perfectly! 

Again thank you for your explanations!

---

