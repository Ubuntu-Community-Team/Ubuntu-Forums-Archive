---
title: "Dual Boot Windows 7 and Ubuntu--Both fail to boot"
date: 2013-12-20
forum: General Help
---

### Post by kwilde on 2013-12-20
After wasting nearly an entire day reading forums in the hope of finding a solution to my problem, I thought I would post here. This is my second Windows 7 and Ubuntu dualboot and while the first install went without a hitch this iteration is causing me nothing but headaches. I installed ubuntu from USB and had Windows and Ubuntu working in harmony for a few days. Then, yesterday I locked my desktop while running Ubuntu--incidentally I was running PostGreSQL Server at the time. Upon attempting to log back in my password simply did not work. Thus, I decided to reboot. Reaching the Grub boot screen successfully I then selected Ubuntu but was prompted with an error message like this: mounting /dev/desk on /root failed: invalid argument. No such file or directory. 

Again, I rebooted this time selecting Windows and it booted successfully. Once again I rebooted, this time from USB, and ran [COLOR=#000000][FONT=Lucida Grande]e2fsck, receiving an error message about superblock. I then [/FONT][/COLOR]ran the commands suggested in this thread: [http://en.opensuse.org/SDB:Clean_the_swap_superblock](http://en.opensuse.org/SDB:Clean_the_swap_superblock). Not only did this not work, now I cannot boot Windows. I get the following error: 

Windows Failed to start. A recent hardware or software change might be the cause. Info: The boot selection failed because a required device is inaccessible.

This is my work computer and I don't have access to the Windows Premium disk so I can't repair it. It's very important I don't lose what's on the Windows drive; I can lose anything on the Ubuntu drives. I'm guessing I unmounted one of the drives, but really have no idea.

I rebooted into Ubuntu from USB and then ran boot repair. After that ran successfully I rebooted Ubuntu and got the following message: The system is running in low-graphics mode. I can access tty1-6, but not 7. Something to do with the graphics loader I imagine. I also can't login using what I know for sure is the correct password. Occasionally I see this message:

"The PostgreSQL server failed to start. Please check the log output. Incomplete startup packet
the database system is starting up
database system was shutdown at
unexpected pageaddr 0/25000000 in log file 0, segment 2, offset 0
invalid primary checkpoint record
invalid secondary checkpoint record
could not locate a valid checkpoint record
the database system is starting up
startup process (PID 1411) was terminated by signal 6: Aborted
aborting startupd due to process failure
starting postgresql server
speech-dispatcher disabled: dit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
checking battery state"

I am really not sure how to troubleshoot any of this, so some general pointers would be very helpful. Thank you! 

Also, this is what fdisk prints out:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xec78060d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000   512987135   255981568    7  HPFS/NTFS/exFAT
/dev/sda3       512989182   976771071   231890945    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       512989184   968642559   227826688   83  Linux
/dev/sda6       968644608   976771071     4063232   82  Linux swap / Solaris

Disk /dev/sdb: 2001 MB, 2001076224 bytes
22 heads, 21 sectors/track, 8459 cylinders, total 3908352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3908351     1954160    b  W95 FAT32

---

### Post by oldfred on 2013-12-20
Just to see where we are at on boot issue.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But Boot-Repair will not fix most Windows issues. You need a Windows repairCD or flash drive for that. If you have access to another Windows 7, just needs to be the same either 32 or 64 bit any version.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I do not know about database corruption. That may be better in a separate thread with that in the title so those that know something will see it.

---

### Post by kwilde on 2013-12-21
Here is the link generated by Boot Repair: [http://paste.ubuntu.com/6612641/](http://paste.ubuntu.com/6612641/)

The first time I ran it (yesterday) it was a much longer process, but I failed to record the URL. Note, dev/sda2 which was originally NTFS is listed as a swap partition. My inkling and limited knowledge leads me to believe that in trying to repair Ubuntu I turned the NTFS WIndows storage to a swap partition.

---

### Post by oldfred on 2013-12-21
The partition table says it is NTFS, but the file system itself seems to have been reset.

I might see if testdisk will let you restore it as NTFS. You do not want to reformat as that will probably erase data.

It may be more like when grub is installed to the partition boot sector which these are fixes for.

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

---

