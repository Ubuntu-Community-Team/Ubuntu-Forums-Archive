---
title: "one HDD won't show in Ubuntu and the other won't show in Win 10"
date: 2016-09-18
forum: General Help
---

### Post by corvettejoez06 on 2016-09-18
OK, I am new and excited to start learning the ways of linux and Unbuntu. I have a Dell XPS with two SEPERATE SSDs installed. What I was "TRYING" to do was have Win 10 on one, and Ubuntu on the other. I wanted to do this so I could have win 10 on "HDD 1" and Ubuntu on "HDD 2". so I could just start/restart normal and NOT be asked where to go (Default Win 10) BUT when I wanted to go to Ubuntu I entered my BIOS Boot options, clicked second HDD and then it would go to Ubuntu. THAT WORKED PERFECT..... except one thing.... when I am in Ubuntu I can't see HDD 1 and when I am in Win 10 I can't see HDD 2. When I go to Win 10, and look at Disk Management HDD 2 is listed as ACTIVE (but NOT NTFS), but NO DRIVE LETTER, and doesn't give me the option to do anything, all options are ghosted. My assumption is the way I installed it made it funny....

How I installed Ubuntu... since I didn't know the specifics of what to make for partitions, I just removed my HHD 1... booted from my USB Drive, then installed Ubuntu directly onto HDD 2... turned off the computer, mounted HDD 1 again... Now I am here! :)

TY
Joe

---

### Post by TheFu on 2016-09-18
Welcome to the forums.

Don't think there is anything in your install that is special.

Windows cannot read most Linux file systems without commercial drivers, which nobody (or very few people) use.  There must be 50 different file systems that Linux can use - that's what happens when anybody who wants to create a new file system to solve their specific issue can do it. Linux doesn't have "drive letters" mainly because the design for how to "mount" - that is the technical term - file systems needed to support hundreds of disks back before Windows 0.9 even existed anywhere. 

Linux can usually see Windows NTFS, vfat and most other file systems no problem, provided the file system is *marked as closed*.  This is just a guess, but did you disable the 2-3 things inside Windows that keep a file system open between boots?  Don't quote me here, but I think MSFT fastboot and MSFT hibernation are causing the problems.  Hopefully, someone else will see this and provide the correct terms, but you can google in the meantime. This is a well-know issue - and I can't blame MSFT for the decision. It is what it is and does make sense for users who don't dual-boot.

Make sense?

---

### Post by corvettejoez06 on 2016-09-18
Thank you for your time! Unfortunately i have no idea what you mean..... This is just a guess, but did you disable the 2-3 things inside Windows that keep a file system open between boots.....
I literally pulled out HDD1 installed ubuntu... put HDD1 back in

---

### Post by TheFu on 2016-09-18
There are settings for the Windows OS. You need to change those while being booted in Windows so it will properly close the NTFS file system when you shutdown the PC.  Also, if you hibernate Windows, it won't work.  The file system must be "closed" - Windows 8 and later leave the file system open and don't really "shutdown" the PC, even when you say "shutdown."  Google is your friend.

---

### Post by corvettejoez06 on 2016-09-18
I tried the "shift" while shutting down and restarting.... that didn't make a difference... I am not getting any warnings, i don't have an issue ONLY see a partitioned part. I can't see the ENTIRE HHD 1 while in Ubuntu and the ENTIRE HHD 2 while in Windows 10.

---

### Post by Mark Phelps on 2016-09-18
Win10 retained a new Hibernation approach from Win8 where, BY DEFAULT, even when Windows is not running, the partitions it uses are still mounted.  That prevents Linux from mounting the partitions.  So, when in Linux, you will not see these partitions on the Windows drive.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by Jimysbil on 2016-09-18
I am not exactly getting your problem here.
What exactly do you mean when you are saying you can't see the drives off the other OS?
When you are booted to Windows you should be able to see your drive from 'Device Manager'.After that you should check your 'Disk Managment' and give a Drive letter to the drive you want to attach.HERE IS THE THING...
If your Windows OS recognises a filesystem it will mount it during boot or when you attach it.In case it does not give it a Drive letter the partition of your disk is probably damaged or it has a not recognizable filesystem from Windows.Linux OSes are usually using ext2,ext3,ext4 and swap filesystems who are not recognisable from Windows.
On the other hand Linux OSes has the ability to mount Windows filesystems (NTFS,FAT,FAT32,XFAT).If you are using Windows 8 or Windows 10, they could have a hibernation technique in order to reduce your boot time.But this technique is making some modifications to your NTFS filesystem and when you are booting from a different OS you can't mount your the hibernated partition.
So I don't think you can't see your hard disk on your Ubuntu but you can't mount your Windows partition.

If this is the problem boot into Windows , open a CMD and type the command:
```
powercfg -h off
```
* It could slow a little down your Windows boot time but you shouldn't have problem to mount your partition on your Ubuntu.
In order you be able to attach an ext4 partition on Windows you should install specific drivers.Anyway I woudn't recoment you do this.

---

### Post by corvettejoez06 on 2016-09-18
> **Mark Phelps said:**
> Win10 retained a new Hibernation approach from Win8 where, BY DEFAULT, even when Windows is not running, the partitions it uses are still mounted.  That prevents Linux from mounting the partitions.  So, when in Linux, you will not see these partitions on the Windows drive.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.
Thank you for your assistance... that didn't help me.

I still don't have access to HDD 1 when I am using Ubuntu and I don't have access to HDD 2 when I am using Win 10

---

### Post by Jimysbil on 2016-09-19
> **corvettejoez06 said:**
> Thank you for your assistance... that didn't help me.

I still don't have access to HDD 1 when I am using Ubuntu and I don't have access to HDD 2 when I am using Win 10

When you are making some registry edits you have to reboot to Windows ones in order those settings take affect.After the second reboot you can boot to Ubuntu and you will probably have access to your partition.
Your Windows OS can't have access to your ubuntu partition(s).

---

### Post by corvettejoez06 on 2016-09-19
> **Jimysbil said:**
> When you are making some registry edits you have to reboot to Windows ones in order those settings take affect.After the second reboot you can boot to Ubuntu and you will probably have access to your partition.

That was already what I was trying, thank you.

---

### Post by westie457 on 2016-09-19
So we can see what has gone wrong to cause this situation boot into Ubuntu and go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Scroll down to the '2nd Option', follow that procedure, copy and paste the commands.
When the Boot Repair window opens **do not** attempt any repairs, click on 'Create BootInfo Summary', post the generated link here.

---

### Post by TheFu on 2016-09-19
A few other guesses :
* Is the Windows drive encrypted or a Windows "dynamic" partition?
* Are the disks in IDE mode?

Refer to this similar issue: [https://ubuntuforums.org/showthread.php?t=1941210](https://ubuntuforums.org/showthread.php?t=1941210)

---

### Post by corvettejoez06 on 2016-09-21
```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   878,136,322   877,110,275   7 NTFS / exFAT / HPFS
/dev/sda3         878,137,344   879,093,759       956,416  27 Hidden NTFS (Recovery Environment)


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   943,435,775   943,433,728  83 Linux
/dev/sdb2         943,437,822   976,771,071    33,333,250   5 Extended
/dev/sdb5         943,437,824   976,771,071    33,333,248  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        983A49C83A49A3DA                       ntfs       System Reserved
/dev/sda2        5A1853C318539CB7                       ntfs       
/dev/sda3        328C3E018C3DC061                       ntfs       
/dev/sdb1        d458ac7f-f775-49f7-b6c5-76b7b071d8f6   ext4       
/dev/sdb5        1c88aaca-bab2-4731-9104-a7186d081985   swap
```

---

### Post by TheFu on 2016-09-21
Please wrap all the output in **code tags** so things line up correctly. That will let more experts view it easily. Hard to read output is ... er ... hard to read and volunteers won't often take the effort to read it.

The boot info output doesn't look funny. It shows 2 500G disks. sda is all Windows.  sdb is all Linux. Both hdds are seen.
Try booting off a live-Boot Ubuntu media (CD/DVD/Flash drive) and look at the storage using the file manager.  Take note of which works perfectly and which has issues using the sda1, sda2 ... nomenclature.

---

### Post by corvettejoez06 on 2016-09-21
So, it appears now Ubuntu is showing both..... But Win 10 still won't

---

### Post by oldfred on 2016-09-21
Windows does not see Linux. 

Users who want to share data between dual boot systems usually create a shared NTFS data partition. In Windows that would be d: and you can mount the NTFS in Linux so readily available.

Also best to set Windows c: drive or its operating system as read only. The Linux NTFS driver exposes all the files & folders that in Windows are hidden to avoid users accidentally doing damage to them.

---

### Post by TheFu on 2016-09-21
> **corvettejoez06 said:**
> So, it appears now Ubuntu is showing both..... But Win 10 still won't

Windows doesn't know how to read Linux file systems. It is seeing the partitions and that is all you can expect without paying for a seldom-used tool on a dual boot system.  Can't recommend any of those tools - never used any. Google should find 1-2 paid options if you must have access to the local Linux storage.

If this question is answered, please mark the thread as **closed** to help others in the community.

---

