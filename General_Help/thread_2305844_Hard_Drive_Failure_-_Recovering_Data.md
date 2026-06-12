---
title: "Hard Drive Failure - Recovering Data"
date: 2015-12-09
forum: General Help
---

### Post by Rab_McNair on 2015-12-09
Hi,

I am currently trying to fix my mum's laptop and rescure her data. She  told me that her laptop was updating Windows 10 when it crashed. Now  when you try to boot up you cannot enter the bios and it is stuck in an  eternal loop where it tries to run repair and diagnostics before  restarting and doing the same again.

I have taken the hard drive out and put it in a docking station which I  connected to my PC. In Windows the drive was not recognised, so I  decided to try it in Ubuntu. In Ubuntu it is seeing some of the drive.  Here is a list of the partitions it sees:

Samsung_rec
Samsung_rec2
860058E50058DDAD
B67AA40D7AA3C887
Windows RE tools

Unfortunately none of the partitions with her data can be seen.

I know there is a chance the data can be recovered in Ubuntu as I have  done it before ages ago. My problem is I have forgotten how to do.

I am currently running Ubuntu 14.04.1 LTS as "TRY IT" and do not have it  installed. I was wondering if someone could help me to try and recover  the data. Tried to use test disk but can't recall how to install. Here  is what I tried in the terminal: 

ubuntu@ubuntu:~$ testdisk device
The program 'testdisk' is currently not installed. You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ testdisk device
The program 'testdisk' is currently not installed. You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ enable universe
bash: enable: universe: not a shell builtin
ubuntu@ubuntu:~$ 

I downloaded it from here: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Thanks

---

### Post by tgalati4 on 2015-12-09
Here is a refresher course:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Connect the laptop with an ethernet cable to the network.  *Testdisk* is in the repositories.

Open a terminal:

```
sudo apt-get install testdisk
man testdisk
man photorec
```

Proceed carefully.  Don't make it worse by running commands that will write to the disk.

If you do find the Windows/data partition, then make a copy of it to another hard drive and recover files from the copy.

---

### Post by Rab_McNair on 2015-12-09
I am unable to connect the laptop to the network as it is unbootable. However, I have removed the HDD from it and am currently trying to access it by connecting it to my PC via docking station and PC is running Ubuntu.

I have actually read that page you linked but don't understand how to install the programs from the repositories. I tried "sudo apt-get install testdisk"

I got this: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ testdisk device
The program 'testdisk' is currently not installed. You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'

Hi,

Just noticed you had added further instruction to your post and I am about to try that and will then proceed to the data recovery page you linked and see how I get on now.

Thought this may be helpful:

Output from sudo parted -l:

```
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   157GB  157GB  primary  ntfs
 3      157GB   315GB  157GB  primary  ntfs
 4      315GB   472GB  157GB  primary  ntfs


Model: NORELSYS 106X (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   839MB  315MB   fat32        EFI system partition          boot
 3      839MB   973MB  134MB                Microsoft reserved partition  msftres
 4      973MB   473GB  472GB   ntfs         Basic data partition          msftdata
 5      473GB   473GB  493MB   ntfs                                       hidden, diag
 6      473GB   474GB  366MB   ntfs                                       hidden, diag
 7      474GB   499GB  25.5GB  ntfs         Basic data partition          hidden, diag
 8      499GB   500GB  1074MB  fat32        Basic data partition          hidden, diag

```
==========================================
The bottom hard drive is the one I am trying to fix. Do you think we can rescue those hidden partitions?

This is the results from me running the commands you suggested:

```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ man testdisk
No manual entry for testdisk
ubuntu@ubuntu:~$ man photorec
No manual entry for photorec

```

Does it matter that I don't have Ubuntu installed and I am just running from LIVE CD?

***Update***

After spending over 2 hours trying to get this to work I decided to install Ubuntu instead of running it from Live CD. After doing this I was able to install testdisk, so it would appear that the program repositry was not available from the LIVE CD.

Going to go and try and clone the drive now before I begin trying to fix the partition and recover the data. Thanks for the help so far. Will let you know how I get on.

***Update 2***

I am having no luck trying to fix this. As far as I can tell the master file table is corrupt as I managed to get into my UEFI, disable secure boot and boot from USB drive with Windows, I then ran chkdsk from command prompt.

In Ubuntu I ran > sudo fsck /dev/sdb & sudo fsck /dev/sd4 before realising they would not work on NTFS

Upon realising that I installed ntfsprogs and ran: > sudo ntfsfix /dev/sdb and got following message:

> Error opening '/dev/sdb': No such file or directory
Volume is corrupt. You should run chkdsk.

I then found a way to check the disk for errors (can't find the command I used) and it is just returning this message: > Warning: read error (EIO) near sector (xxxxxxxx) , skipping. This is still running and I am waiting to see the end message. Just completed there and end message is > *** Fatal error: dev(/dev/sdb): seek failure.

While I have been waiting for that to complete, I have been doing further reading and came across this: [http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

The sections that are of interest to me are: > Recovering An NTFS Boot Sector On An NTFS Partition Using Its Backup and > Rebuilding An NTFS Boot Sector On An NTFS Partition. However, I do not understand how to do what they are suggesting. Could someone talk me through this please?

I have also been trying to use gddrescue and have got as far as installing, opening and reading help but I am scared to run it as I know it can wipe things if you don't know what you are doing. Therefore, I was wondering if someone would be kind enough to talk me through it or show me where I can find a guide for dummies like myself.

Thanks

---

### Post by kurt18947 on 2015-12-10
Have you created a backup of the partition containing the data you want to recover? You don't want to go from "difficult but maybe possible to recover" to "No bloody way I'm going to recover anything from this mess" on the only version in existence. I have no expertise in what you're trying to do but did experiment with test disk/photrec on a flash drive. It did recover files - including some that were present on the same drive from when it was a FAT32 partition before being formatted to ext2. The files I gave it time to recover were intact but no recognizable names and no recognizable order. I ran out of patience and had a current backup so didn't let the process finish. I installed testdisk on the hard drive and ran it on a flash drive. If I recall correctly it stored the recovered files on the same partition as testdisk was installed on. I don't really recall that much, it was some time ago and not a high priority task.

---

### Post by Rab_McNair on 2015-12-10
While I would like to recover the data, my problem has changed as it now looks like the HDD has a corrupt master file table.

I have tried to backup the drive using this command: > **[FONT=courier new]sudo ddrescue -v -n /dev/sdb /dev/sdc ddrlog.txt[/FONT]** which did not work and I got this message: 
> 
ddrescue: Output file exists and is not a regular file.
ddrescue: Use '--force' if you really want to overwrite it, but be
          aware that all existing data in the output file will be lost.
Try 'ddrescue --help' for more information.

I also tried just doing the missing partition which has Windows: > **[FONT=courier new]sudo ddrescue -v -n /dev/sdb /dev/sdc ddrlog.txt[/FONT]** and got the same message

---

### Post by tgalati4 on 2015-12-10
Try using partition names.  /dev/sdb  is an entire device, not a partition.  /dev/sdb1 is the first partition on device /dev/sdb.  /dev/sdb2 is the second partition on the device /dev/sdb.

It's been 10 years since I've used NTFS, so I can't really help with NTFS recovery.

---

### Post by stalkingwolf on 2015-12-10
try running the hard drive regenerator ob the hirens disk  you can get it here.  [http://www.hirensbootcd.org/]("http://www.hirensbootcd.org/")

i have had great success with this tool.  you should then be able to find and save the data.    might even fix the drive completely.

---

### Post by Rab_McNair on 2015-12-10
Thanks for the advise, will try all the suggestions soon and let you know how I get on. Really appreciate you taking the time to assist.

---

### Post by dragonfly41 on 2015-12-10
Reading your first post you are trying to recover a Windows 10 installation.

You also have Windows.

Although you are now up to your neck in an alligator pit I do suggest that you rethink your plan and perhaps stay with your Windows to recover your mum's Windows.

I have a dual boot drive with an older version of Windows and I've used "Recover My Files" from GetData.com .. [http://www.getdata.com/](http://www.getdata.com/) .. quite successfully.

The only problem with this approach is that Windows recovery tools are often not free (as in Ubuntu) .. but you can run an evaluation licence just to test if the data is recoverable.

---

### Post by Rab_McNair on 2015-12-10
> **dragonfly41 said:**
> Reading your first post you are trying to recover a Windows 10 installation.

You also have Windows.

Although you are now up to your neck in an alligator pit I do suggest that you rethink your plan and perhaps stay with your Windows to recover your mum's Windows.

I have a dual boot drive with an older version of Windows and I've used "Recover My Files" from GetData.com .. [http://www.getdata.com/](http://www.getdata.com/) .. quite successfully.

The only problem with this approach is that Windows recovery tools are often not free (as in Ubuntu) .. but you can run an evaluation licence just to test if the data is recoverable.

In the past I usually do the recoveries I have had to do using Windows applications. Have used Ubuntu 1-2 when I have not been able to recover in Window.

My problem is that the drive is just not getting noticed in Windows and is not even responding to commands I enter in CMD. That is why I have switched to Ubuntu.

---

### Post by dragonfly41 on 2015-12-10
You can install and try testdisk running in Windows.

---

### Post by Rab_McNair on 2015-12-11
Sorry for delay in replying as I don't really have much to update at the moment. As someone suggested I burned Hiren's recovery disk and am currently using a tool that searches hard drive for bad sectors and tries to recover them (was one of the few tools that I could get to work). So far it has processed about 1/3 of the disk in 24 hours and over 1000 bad sectors have been recovered.

My hope is that it recovers the MFT from a bad sector and I can get in and retrieve my mum's data. If that works my plan was to wipe the disk with 1s or 0s and use it for a week and then check if there were any new bad sectors. If there are bad sectors it is going in the bin but may keep for a backup drive if no new bad sectors found.

---

