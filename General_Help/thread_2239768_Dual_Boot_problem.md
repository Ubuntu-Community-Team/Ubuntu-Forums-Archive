---
title: "Dual Boot problem"
date: 2014-08-15
forum: General Help
---

### Post by Liamdale on 2014-08-15
I have installed linux ubuntu (12.04) in a dual boot configuration with windows Xp.  All has gone well until today when I tried to access the windows drive from ubuntu (windows drive C:)

My dual boot configuration:  Windows Xp remained on drive C: and Ubuntu was installed on drive D: (second hard disk).  This latter drive was divided into two general aprtitions /dev sdh1 for data (both widows and linux) and /dev/sdh2,3,5,6 for linux os and data.

My problem: when trying to acces the windows drive (os and data), what windows calls the C; drive, ubuntu could not mount the drive and I received the follwing message:

Unable to mount Phil (drive name)
Error mounting: mount exited with exit code13: ntfs_attr_pread_i: ntfs_pread
failed:input/output error
Failed to read NTFS $Bitmap:input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.  In the first case run chkdsk /f on Windows
then reboot into Windows twice.  The usage of the /f parameter is very
important!  if the device is a SoftRAID/FakeRAID then first activate 
it and mount a different device under the /dev/mapper/directory, (e.g.
/dev/mapper/nidia_eahaabcc1).  Please see the 'dmraid' documentation
for more details.

I tried rebooting into windows but can't.  The Windows logo appears and the system resets automatically.  I have tried using the f8 menu, get windows safe mode menu but still get a computer reset process

I assume the the windows boot sector is damaged but how to repair it from ubuntu.  If I use my windows installation disk, I assume that I will mess up my system even more.

Can ChkDsk be used from ubuntu?
Can I use windows installation disk to get a C: prompt?  and if yes will this mess up my system.

I have been reading on grub and have realized that the system automatically boots into ubuntu and a series of linux script files create a grub.cfg file which create the grub menu I see on my screen

Any help would be appreciated

LiamDale

---

### Post by oldfred on 2014-08-15
I am not sure I understand configuration as d: is a Windows convention. If not another partition but another drive is it an external drive. Usually it would not be sdh otherwise.

You can only run chkdsk from Windows or a Windows install or repair disk.

Most repairs for Windows from Linux are just to get it booting again. But you you can get to repair console, then you need a Windows repair CD or flash drive.

It should not have been booting directly to Ubuntu unless your XP install never was seen from Ubuntu. Its os-prober should have found the XP install. Do you have grub installed to MBR of sdh? And still have Windows boot loader installed to your sda drive? If not use Boot-Repair to change that, but it cannot run chkdsk nor most other Windows repairs.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can post link from running the Boot info report from Boot-Repair just to see if configuration looks correct.

---

### Post by Liamdale on 2014-08-15
I am still new to Linux and still studing the OS.

   I used the windows drive conventions in an attempt to show that I have windows installed on one phyiscal drive and Linux on another.  From what I understand about grub is that it replaces the MBR with its own code and points to   /boot/grub/grub.cfg ,  /etc/grub.d/ and /etc/default/grub.  If I boot with my windows installation disk will it overwrite the Master Boot Record and change the system back to a Windows only OS or will it only repair (re-install) windows on the C: drive.

 

 I have three hard disks on my system:
 

  The partition setup,  using GPart


[TABLE="width: 500"]
[TR]
[TD]Windows notation[/TD]
[TD]Linux notations[/TD]
[TD]Size[/TD]
[/TR]
[TR]
[TD]Drive C:[/TD]
[TD]/dev/sdg[/TD]
[TD]322 GiB    contains Windows OS[/TD]
[/TR]
[TR]
[TD]Drive D:[/TD]
[TD]/dev/sdh1[/TD]
[TD]468 GiB               Data partition[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/dev/sdh2 (ext4)[/TD]
[TD]20 GIB  contains  Linux OS[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/dev/sdh3 (extended)[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/dev/sdh5[/TD]
[TD]8 GiB   Linux swap[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]/dev/sdh6[/TD]
[TD]435 GiB  Data[/TD]
[/TR]
[TR]
[TD]Drive E:[/TD]
[TD]/dev/sda[/TD]
[TD]2.73 GiB  NTFS drive for backups and added data space[/TD]
[/TR]
[/TABLE]

All the drives C:,D:, and E: are physical hard drives

I did not think that I could have used ChkDsk in ubuntu but I had to ask the question.

How to repair the windows boot drive safely ?

I will still want to use a dual boot for a while but my future plans are to have a new computor with only linux and this current computer with windows xp setup in a network.

Liamdale

---

### Post by yancek on 2014-08-15
The link below explains how to repair the mbr of the windows disk.  If you don't like it, just google as there are countless other sites with similar info.  You need to make sure you get the correct dirve, the one with windows on it.  This won't 'reinstall' windows, just repair the boot files.  You will then need to install Grub to the mbr of its drive.  You should then be able to select which drive to boot windows/Linux on boot.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

The link below is a How-To install Ubuntu 14.04 but the first part of it has a lot of useful information on Linux in general, partitioning and dual-booting.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Liamdale on 2014-08-15
Thanks yancek;

I've read both sites and saved them for future  reference.  I don't think my MBR is damaged because I can boot linux  without any difficuly.  This may be my final approach if I can't  discover how to repair my windows boot sector.  If I go in this  direction, I suspect that windows xp will rewrite the MBR and point to  my C: drive which has Windows already installed, correct the problem but  Linux will not be available.  Then I can reinstall a dual boot with linux  ubuntu 14.04.  The partitions on my second hard drive are already there.

Am I wrong?

LiamDale

---

### Post by LostFarmer on 2014-08-15
If you get to the XP logo , I would say it is very unlikely the boot record is bad.  But to verify you can install in linux 'testdisk' , under the advance option it will check the boot record.  Check out [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) , it has a mini XP you can use to run chkdsk and testdisk plus other tools.  The last time I use the cd was 5 years ago and much has change on it.

---

### Post by oldfred on 2014-08-15
With multiple drives, you have multiple MBRs. So you can have different boot loaders in every MBR. 
Best to have each system on different drive and its boot loader on that same drive. Or that the drive would work without any other drive at least to boot even if data partition(s) may not mount. Since grub can boot multiple systems you then set BIOS to boot Ubuntu/grub drive. But can have another grub on another drive.

Windows has to have its boot loader in the MBR of the Windows drive. All the Windows MBR does is check which primary partition has boot flag and jump to the partition boot sector or PBR to continue booting Windows. Grub boots Windows by skipping the MBR and jumping directly to the PBR.

If you use Boot-Repair do not run Auto fix. That just installs one grub to every MBR. Typically you want Windows on Windows drive and maybe other boot loaders on other drives. It does that as some users do not know or do not reset BIOS to correct drive to boot. With grub in every MBR then grub should boot no matter what. You can used Advanced options and choose which boot loader to install and which drive to install into.

---

