---
title: "Windows won't detect my HD after running Boot-Repair [DUAL BOOT/ Win7/Ubuntu]"
date: 2017-05-25
forum: General Help
---

### Post by jkuwajima on 2017-05-25
Dear Ubuntu Community

I have been using Ubuntu 16.04 alongside Windows 7 very smoothly for several years. But something went wrong and after using Boot-Repair to restore the GRUB load Menu. 

I-)I can't load Windows 7 anymore;

II-)After trying to restore Windows 7 using the Installing Disk, I noticed that it was unable to detect the Hard Disk and the partition where Windows 7 supposed to be installed.

III-) But Ubuntu still detects the OS Partition

IV-) I runned GParted to try to see what happened this messaged poped-up:

> "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes."

After exploring my OS Partition (/dev/sda3)I found this Warning message:

> "[I]Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs[/I]."

V-) GParted was unable to solve repair file system (nfts) on /dev/sda3;

VI-) Additional information:

> Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdd6865b6

> 
Device         Boot            Start        End    Sectors  Size Id Type
/dev/sda1               63               80324      80262 39.2M  6 FAT16
/dev/sda2            81920          25563135   25481216 12.2G  7 HPFS/NTFS/exFAT
/dev/sda3         25563136     1332019199 1306456064  623G  7 HPFS/NTFS/exFAT
/dev/sda4       1332021246 1465147391  133126146 63.5G  5 Extended
/dev/sda5       1400381440 1431629823   31248384 14.9G 82 Linux swap / Solaris
/dev/sda6       1431631872 1465147391   33515520   16G 83 Linux
/dev/sda7       1332021248 1400381439   68360192 32.6G 83 Linux

> Partition 1 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.


Please could anyone assist me? I'm at the end of my rope here

How could I restore Windows 7 and fix my problem ?

I also posted this on Ask Ubuntu
[https://askubuntu.com/questions/918657/window-cant-detect-hard-disk-after-trying-to-repair-dual-boot-via-boot-repair](https://askubuntu.com/questions/918657/window-cant-detect-hard-disk-after-trying-to-repair-dual-boot-via-boot-repair)

---

### Post by yancek on 2017-05-25
The important missing factor in your post is the "something went wrong".  Some hint as to what happened could help.
Why did you feel the need to use boot repair?   Your post implies that you were able to boot windows until after you ran boot repair, is that correct?
Boot repair has an option to "Create BootInfo Summary" which is usually the best option to select.  When it finishes, it will show a link which you can post here and members can view the information and make suggestions.

> After trying to restore Windows 7 using the Installing Disk, I noticed  that it was unable to detect the Hard Disk and the partition where  Windows 7 supposed to be installe

That's pretty weird, especially considering that your Ubuntu does detect the proprietary windows filesystem.
If a windows filesystem is somehow corrupted, you would usually need to run chkdsk from a windows installation DVD with the Repair option.  There really isn't any Linux software to repair ntfs filesystem due to their proprietary nature.  ntfsfix might do very minor repairs but it's highly unlikely it or GParted will be able to repair whatever problems you have on the ntfs partition.


> *The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs*." 			 		

The above quote indicates you need to install that specific software in Ubuntu.  Have you done that?

---

### Post by oldfred on 2017-05-25
You have a newer 4K drive.
Sector size (logical/physical): 512 bytes / [COLOR=#ff0000]4096 [/COLOR]bytes
But your first partition starts at sector 63. Partition tools have not used 63 since XP era. Windows 7 was first to change, and gparted about a year after Windows 7.
/dev/sda1               [COLOR=#ff0000]63 [/COLOR]              80324      80262 39.2M  6 FAT16

Did you copy drive from old system? Or use some very old partition tools to partition drive?

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

One user who saw the small 1MB gaps that the larger sector size may now show, wanted to edit those and in effect destroyed system.
So whatever you do make sure you have good backups.
Moving start & size of NTFS partitions requires chkdsk immediately after.
And moving start of a partition can be a very slow process depending on amounts of data. Any interruption and all data is lost.

---

### Post by Michael_McKenney on 2017-05-25
I stopped dual booting because repairing one OS usually broke another.  I usually find older hardware for Linux to run on.

---

### Post by LastDino on 2017-05-25
```
The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes 
```

This particular error has occurred to me for sdb (Live USB) which I resized partitions on which damaged first few sectors. I'm little surprise that this has happened to "sda". In my case Gparted would show 2Xwhatever size the pendrive was. i.e 16GB was shown as 32 one and 32 one was shown as 64 one.

     
 

What operations did you perform before getting this error? 

Solution to this problem is not easy and may involve over writing damaged sectors with "0", and that is extremely risky as it is done with "DD". 

Therefore, be extremely sure what is causing this, on USB I simply formatted the thing, but on sda that wont be an option either.

---

### Post by jkuwajima on 2017-05-25
Hi Yancek!

Every now and them I need to restore the Boot Menu, because the Windows Boot option vanishes... Specially if there is an Ubuntu Base Update or Upgrade.
I´ve fixed it several times using Boot-Repair through a Live-USB.
Last time wasn´t really different..I ran Boot-Repair, because I made some updates and I could no longer able to boot Windows.

I´ll try to "Create BootInfo Summary" and post it later when I come back from work.

Do you think it has something to do with Boot-Flag? I saw that option on Boot-Repair where you choose to repair Windows Files... What does a Boot-Flag do?

---

### Post by jkuwajima on 2017-05-25
Hi Oldfred

No I have not copied it from an old system. Well I have been using a dual-boot since 2013 and specially after Ubuntu-base updates or upgrades I have to run Boot-Repair in order to be able to boot Windows again.
As I posted before, I run Boot-Repair on my computer like evereytime before, but now I can´t even repair Windows using the Installation Disk because it can´t detect it.. Strangelly Ubuntu does detects and read all the OS files.
I don´t remember choosing any different option while running Boot-Repair.

---

### Post by jkuwajima on 2017-05-25
I guess formatting it would be my last resort... 
Do you know how Boot-Flag works?

---

### Post by yancek on 2017-05-25
If your windows 7 is the default using MBR (rather than UEFI) then you would need to have the boot flag set to the windows partition with the boot files, probably the system partition and this needs to have boot files on a primary partition.  That should have already been set up when windows was installed unless it changed somehow?   The boot flag is irrelevant for every Linux system I am aware of.  Best to post the boot repair output.

---

### Post by oldfred on 2017-05-25
Windows, but not grub uses boot flag with MBR partitioning which Windows must use with BIOS boot as yancek has said.

Some Linux boot loaders like syslinux and lilo also use boot flag for BIOS boot. 
A few BIOS also do not even let you start booting unless a primary partition has a boot flag. So we still suggest having one on a primary partition.

Windows 7 or later default install is a 100MB boot partition and main install. Since most Windows users never see the Windows boot partition, they often delete it. So Boot-Repair often copies boot files from boot partition to main install. Then grub which just looks for boot files not boot flag, adds a second boot entry into grub menu.

With UEFI/gpt boot flag has a totally different meaning, it is just used to set GUID info for UEFI to internally know which partition has UEFI boot files. The same partition is used/shared by all UEFI based boot loaders.

I do not know how you would have a start at sector 63. Perhaps you used an older Linux or third party tool to partition. As by 2012 Windows 8 was out and Windows 7 had been used for years. And Linux partitioning tools had also long prior converted to use start sector of 2048 for compatibility with newer 4K and SSD type drives.

---

