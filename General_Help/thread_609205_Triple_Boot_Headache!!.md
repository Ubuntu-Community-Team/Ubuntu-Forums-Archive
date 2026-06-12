---
title: "Triple Boot Headache!!"
date: 2007-11-10
forum: General Help
---

### Post by Route490 on 2007-11-10
Ladies and Gents,

I am new to Ubuntu and had just got it all setup running the way I liked it, so of course, it was time to move on and break something else!

I have just installed openSUSE 10.3 to give it a whirl but thanks to my lack of knowledge I am now unable to boot Ubuntu/windows XP/openSUSE as I keep getting error 21 from the grub! :(

My setup consists of 4 HDDs

HD0       /dev/sda1      Windows XP      

HD1       /dev/sdc1      Ubuntu                
              /dev/sdc5      Linux Swap

HD2       /dev/sdd1       200GB NTFS Drive

HD3        /dev/sdb1      400GB NTFS Partition
              /dev/sdb2      OpenSUSE 10.3

Now i thought I understood the grub....I choose to install the grub (stage1) in the MBR of hd0 and then set hd0 as the first boot device.  But it just gives me the error 21!

I now basically have two grub folders, One in the Ubuntu drive and one in the openSUSE, with 2 different menu.lst! (if only i could get far enuough to see them at boot up) All too confused now.......

What am i missing? ANY information would be much appreciated!

Thanks
Paul

---

### Post by confused57 on 2007-11-10
Have you tried setting your hard drive boot order back to how you had it when you installed Ubuntu?
If you have and still can't boot your computer...leave the boot order as you had it originally, then use the Ubuntu live cd to reinstall Ubuntu's grub IPL to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If this enables you to boot Windows & Ubuntu, you can add a configfile entry to Ubuntu's menu.lst to boot OpenSuse:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by Route490 on 2007-11-11
Many thanks confused57...I didn't have much luck with reinstalling grub (probably more my fault tho) but I did eventually find Super Grub Disk, Which at least got me back to being able to boot Ubuntu/XP

Now not to be cheeky, knowing this is the ubuntu forums after all...But does anybody know what details I should add to to menu.lst in order to make openSUSE boot from the grub.

I have tried adding
title openSUSE 10.3
    root (hd3,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_WDC_WD5000AAKS-_WD-WCAPW4251565-part2 vga=0x31a    resume=/dev/sdc5 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

Which I copy and pasted from the openSUSE menu.lst but it comes back disk not found!!!

Is this just a problem with the root part of the above? or something to do with all the kernal stuff which I do not understand in the slightest!! haha

I would be interested to see other peoples menu.lst who boot openSUSE
Thanks

Paul

---

### Post by confused57 on 2007-11-11
Glad you were able to get Super Grub Disk to work, it's a handy utility to have for booting issues.

You could try the configfile entry to boot Suse:
```
title  OpenSuse 10.3
configfile (hd3,1)/boot/grub/menu.lst
```

I'm not sure if OpenSuse uses menu.lst or grub.conf.
You might want to check the output of:
```
gedit /boot/grub/device.map
```
this will show if Ubuntu recognizes your Suse drive as (hd3)
and:
```
sudo fdisk -l
```
for your partitions...(hd3,1) is the 4th hard drive, 2nd partition.

You can always mount your OpenSuse root partition with the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then you explore the Suse menu.lst(or grub.conf?) for the correct entry

---

### Post by Route490 on 2007-11-11
Confused57, always one step ahead....

They both use menu.lst.  The openSUSE menu.lst has root (hd3,1) for its location, But when I try this in the grub I still get the drive not found. If i tab to get the possibilities it says hd0, hd1, hd2. No mention of my 4th hard disk!

I have edited both device.map to look like this (ubuntu and openSUSE)

(hd0)	/dev/hda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sda

This was my attempt at making things simple for me. (no idea why I didn't make it a,b,c haha)

sda2 is the openSUSE partition. 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       46817   376057521    7  HPFS/NTFS
/dev/sda2           46818       60801   112326480   83  Linux


So even when i try the code you suggested, which I believe is right, it can't find the drive hd3,1

I have mounted the openSUSE drive in Ubuntu so can easily edit files but am running out of ideas....

Am starting to regret ever cheating on Ubuntu! lol

Paul

---

### Post by confused57 on 2007-11-11
I missed that you had already copy & pasted Suse's menu.lst to your Ubuntu grub...have you tried changing (hd3,1) to (hd2,1)?

Here's some possible solutions for error 21:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

I don't know about SATA drives, but for IDE drives the hard drive controller in bios must be set to "Auto" or "Enabled".

---

### Post by Route490 on 2007-11-12
I am finally triple booting :) 

This may have been obvious to some but turns out the problem was that my BIOS was unable to see my 4th hd which had openSUSE due to the fact this was plugged in via a PCI adapter and not directly in to the motherboard!!

Got there in the end......Thanks for your help confused57, at least if nothing else I now understand how NOT to install an OS :lolflag:

Paul

---

### Post by confused57 on 2007-11-12
> **Route490 said:**
> I am finally triple booting :) 

This may have been obvious to some but turns out the problem was that my BIOS was unable to see my 4th hd which had openSUSE due to the fact this was plugged in via a PCI adapter and not directly in to the motherboard!!

Got there in the end......Thanks for your help confused57, at least if nothing else I now understand how NOT to install an OS :lolflag:

Paul
Glad you were able to get your triple boot working.  Hard drive PCI adapters don't usually work with Ubuntu...

---

