---
title: "Grub installation problems"
date: 2017-03-23
forum: General Help
---

### Post by magnusnm on 2017-03-23
[CENTER][FONT=verdana]Hello[/FONT][/CENTER]
[FONT=verdana]I'm trying to dualboot ubuntu 16.04 64 bit using USB to install from. I've tried going through the installer several times, 2 different USB drives, made several partitions and disk checks, but every time i get the same error at the same time.

I have an SSD as my windows drive and a 1 TB HDD I'm trying to install the ubuntu OS onto.

[/FONT]
[FONT=verdana]I have no idea what to do at this point: anyone who has some pointers?[/FONT]
[FONT=verdana]I did some kind of troubleshooting I saw recommended on another forum, url is here:[/FONT]
[FONT=verdana][http://paste2.org/e7L0sg5E](http://paste2.org/e7L0sg5E)[/FONT]

---

### Post by oldfred on 2017-03-23
You did something very unusual on sdb
> Logical Disk Manager (LDM) data partition (Windows)

Windows developed a logical partition system for the old BIOS/MBR as that has a 4 primary partition limit.
And they called that dynamic partitions to allow more than 4 partition. Most systems used what Windows called "Basic" and then converted one primary to extended to add many logical partition.

But with new UEFI systems using gpt, your limit on partition is 128, so no dynamic partitioning is required.
How did you end up with the LDM? I have seen somewhere that with gpt dynamic would be called LDM.

If you want to install Ubuntu on sdb, you have to remove the LDM. Have seen many users use the third party tools with SFS/dynamic to convert back to standard partitions. But yours is the first with LDM.

 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

---

### Post by magnusnm on 2017-03-23
Yes, my D: drive is dynamic for some reason. I think I accidentally converted it while trying to extend it with some of the unallocated disk space from my previous attempts. I'll try running those 3rd party tools to see if they'll help, however I am pretty sure that I got the error before it became dynamic as well.

I'll try to convert it back and see if it helps and get  back with the result, thank you for the in depth answer!

---

### Post by magnusnm on 2017-03-23
[https://photos.google.com/share/AF1QipOuoZU-zL5PDJx1PGfsvE160ksrqBeTvSYiDN07mPYjJZPmTl439qWdWRaxU8IoWQ?key=bnlsQ0o1YktpYXlvYVp3T29sTmdLaTZJNXh0bFdn](https://photos.google.com/share/AF1QipOuoZU-zL5PDJx1PGfsvE160ksrqBeTvSYiDN07mPYjJZPmTl439qWdWRaxU8IoWQ?key=bnlsQ0o1YktpYXlvYVp3T29sTmdLaTZJNXh0bFdn)

Getting about the same error, even though it looks slightly different. I ran an error check before trying to install and it said 0 errors.

[https://imgur.com/a/6UUJk](https://imgur.com/a/6UUJk)

Do you think it'd make a difference if I manually chose the installation drives? "Do something else" in the installation wizard?

---

### Post by oldfred on 2017-03-23
Are both drives gpt?
post this:
sudo parted -l

You can run Boot-Repair's advanced mode and do the full uninstall reinstall of grub. But you must be installing in UEFI mode.
You may have been trying to repair grub in BIOS mode which requires different partition to install correctly (bios_grub).
But you want to install Ubuntu in UEFI mode.
In Boot-Repair select advanced mode and total uninstall/reinstall of grub-efi-amd64. If it says grub-pc that is the BIOS version.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by magnusnm on 2017-03-23
If gpt means basic, yes

Can I post it from the "trial run" of Ubuntu?

How do I know if I'm in UEFI mode or BIOS mode? Is that an option in BIOS?

---

### Post by magnusnm on 2017-03-23
[http://pastebin.com/yunvw3h5](http://pastebin.com/yunvw3h5)

parted -l

I just saw your appendix on your posts, I'll check it out immediately

---

### Post by magnusnm on 2017-03-23
I received these after running the advanced boot repair:

[http://pastebin.com/ZFyUYEsE](http://pastebin.com/ZFyUYEsE)

And this massive thing, seems like there's a summary at the top

[https://justpaste.it/14s2f](https://justpaste.it/14s2f)

---

### Post by oldfred on 2017-03-23
Grub install had error, related to 
Locked-ESP detected.

It looks like it tried to run the dosfsck and fsck on other partition and had further issues.

Try this again and see if you still get errors.
Must be unmounted:
 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck 
I believe this actually is same command (one links to other):

 Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

In a few cases we have had to backup all the files in the ESP and erase it, Then recreate new ESP, FAT32, with boot flag & restore all the files.
Best to backup ESP, sda1 anyway as it has Windows boot files and often other backups do not include ESP.

What model Lenovo?
Some have required UEFI updates.

       
 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 
           
 T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by magnusnm on 2017-03-23
It's a y700 - everything else is quite out of my reach. No clue what "unmounted" means or what it is that's supposed to be unmounted and where, how to find the variable to pass as the fat 32 device

I might have to wait for a ROS port to windows, I really don't seem to be cut out for linux. I'll try to look into those links and read up on more stuff tomorrow, thank you a lot for the help so far

---

### Post by oldfred on 2017-03-24
In Linux you mount or unmount a partition or device. 
Windows typically automounts partitions but auto assigns letters like d:, e: that are not very useful.
With Linux we can create mount point with any name/label we want and then manually mount a partition/device to that mount point.
Nautilus, the file browser will auto mount partitions, but often uses UUID if not otherwise labeled.

So to make sure your ESP is not mounted, just do not click on it with Naulitus to see what is in it. And do not manually mount.

This showed the command you needed.
Must be unmounted:
 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

The /dev/sda1 is your ESP - efi system partition which is formatted FAT32 and then is a fat32 device.

---

