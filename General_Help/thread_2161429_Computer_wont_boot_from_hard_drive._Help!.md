---
title: "Computer wont boot from hard drive. Help!"
date: 2013-07-10
forum: General Help
---

### Post by ka2012 on 2013-07-10
About a week ago, I decided to dual boot my computer between windows 7 and ubuntu. I partitioned my hard drive, and they were both working (I had 4 primary partitions, System, Windows 7, Ubuntu, and recovery). I was trying to add another partition(which I now realize you cant do with mbr) and I accidentally converted my entire hard drive to simple volume. My computer wouldnt boot, so I booted it from the usb that i have the ubuntu install on. I used the program testdisk to convert my hard drive back to a basic disk. Now, it still wont boot up, and gParted says that the entire drive is unallocated space.

<snip> base64 code removed

The recovery partition isnt working (I think because it got turned into a logical partition inside of an extended one when I converted back to a basic drive). I have no idea where my ubuntu partition is...the file space got turned into the one called storage, and now all it has in it is a recycle bin. Ubuntu is free, so i can just reinstall it if I have to, but I would like to get my computer to boot up and windows to work. I know the simplest thing to do would probably be to back everything up and then just wipe the hard drive and make a new partition table and reinstall everything, but I would rather not do this if there is any other way. Any suggestions or opinions on how to fix this?!?!?

---

### Post by oldos2er on 2013-07-10
Please start a new thread, and don't use base64 images.

---

### Post by coffeecat on 2013-07-10
@ka2012, you triggered a firefox bug by dragging and dropping an image into the editor box, and this converted your image into base64 code. You can't post images that way. Please use the manage attachments buttons which you'll find under the message editor box in advanced mode to upload images to the forum.

I've edited the base64 code out of your post because it causes some browsers to freeze.

---

### Post by oldfred on 2013-07-10
Windows tools usually work better to convert dynamic back to basic. And you can have more than 4 partitions but have to use one of the four primary  as the extended and create as many logical partitions as you want inside the extended.
Not sure how testdisk converted your partition table. NTFS partitions on drive must have PBR or partition boot record or sector with size info that matches partition table. If your Windows NTFS partition(s) has same start and size as originally it should work.

May be best to best to see details. Do you have a Windows repairCD? That may be needed.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ka2012 on 2013-07-12
Sorry, I screwed up with the pictures...when they got deleted there was also a chunk of text in the middle that got deleted...so i'm pretty much reitterating it, but adding pictures...

About a week ago, I installed ubuntu 12.04 to my computer (I already had  windows 7, so i dual booted them). They were both working fine. I was  trying to add another partition that I coulld use for storage, but I  already had 4 and I accidentally converted my entire hard drive to  simple volume. My computer wouldn't boot, so i'm booting from the live  usb that I used to install ubuntu. I used the program testdisk to  convert my hard drive back to basic volume(I think). Now, It still wont boot up  and gparted shows the entire space as unallocated.
[ATTACH=CONFIG]244654[/ATTACH]
But all of my  data and partitions are still there because if I go into disk manager,  it shows them. I think my ubuntu partition got replaced by the storage  partition I was going to make, and my linux swap space and recovery  partition are in an extended parition.
[ATTACH=CONFIG]244653[/ATTACH]
I can acctually access all of my files, I just can't boot.
[ATTACH=CONFIG]244655[/ATTACH]
I  can reinstall ubuntu if I have to, since its free and I've only had it  for like a week, so there's not really any data or programs on there  yet, but I would like to get my computer to boot and windows to work,  since pretty my all my programs and settings and stuff are on there. I  know I could probably back up everything, then create a partition table  and reinstall everything, but I would rather not do this. Any  suggestions or opinions?


p.s.: I ran boot info and got this:         [http://paste.ubuntu.com/5869272/](http://paste.ubuntu.com/5869272/)

---

### Post by oldfred on 2013-07-12
There is no Linux partition shown. Did testdisk have a Linux formatted partition you could recover.

You also must fix this error.
       /dev/sda4 ends after the last sector of /dev/sda

Testdisk still uses CHS - cylinders, heads, sectors but drives have converted to LBA or large block allocation. The conversion sometimes rounds up and testdisk writes extended partition beyond end.

You can use fixparts to correct error.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by ka2012 on 2013-07-12
Ok, I used fixDisk and it corrected the extended partition problem. My partitions are still all messed up though. My ubuntu is nowhere in sight, but I think it got replaced by the storage partition when I tried to make that (all that the storage partition had in it was a file called recycleBin). The computer still wont boot up, either. Before, the computer used to turn on, show a screen that the displayed the hp logo, then turn black and go to the screen where I could boot windows or ubuntu. Now it just stays on the hp screen. Do I have the boot flag on the wrong partition or something? Heres a screenshot of gParted:
[ATTACH=CONFIG]244663[/ATTACH]
sd1 is system
sd2 is my windows 7
sd3 used to be ubuntu(I think ubuntu got turned into ubuntu because, before, ubuntu occupied that many GB of space)
sd4,5,6 self explanatory

I really don't mind if I have to reinstall ubuntu, because I don't really have much data on it anyways, since I only dual-partitioned my hard drive a week ago, I just want to get my computer to boot up

---

### Post by oldfred on 2013-07-12
While a small part of the grub2 boot loader is in the MBR, most of it is in the Ubuntu partition. Without the Ubuntu partition grub will not boot.
You can restore a Windows boot loader to the MBR, but if installing a new UBuntu install that will overwrite the MBR and give you a new working grub.

You need to sort out partitions that you want. I often suggest smaller system partitions for both Windows & Ubuntu and larger data partitions. To share any data between systems you should have a shared data partition formatted NTFS. All but the Windows boot partition can be logical partitions inside the extended. Windows only boots from a primary partition.
Only use Windows to shrink the Windows partition, but use gparted to create or change all other partitions.

---

### Post by ka2012 on 2013-07-12
Im sorry, I found the first paragraph a little confusing. So you're saying that if I reinstall ubuntu, the grub menu should work and I will be able to boot windows and ubuntu?

---

### Post by oldfred on 2013-07-12
Correct. A new install reinstalls grub2's boot loader to the MBR and has all the rest of grub in the new install. Best to use manual install or Something Else to choose which partition is / and its format, which is /home and its format etc.

If you just want to get into Windows quickly you can install a Windows boot loader. You should have both Boot-Repair and a Windows repairCD so you can fix most things. I like to have Supergrub, Knoppix, PartedMagic, gparted as liveCDs so I have multiple ways to boot or repair a system.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

for MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by ka2012 on 2013-07-13
I reinstalled ubuntu and bow both windows and ubuntu are working fine! I will be sure to reformat my drives as you suggested sometime soon, im just happy i got my computer working again! Thanks for the help!

---

