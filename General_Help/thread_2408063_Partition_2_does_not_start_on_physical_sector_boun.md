---
title: "Partition 2 does not start on physical sector boundary."
date: 2018-12-13
forum: General Help
---

### Post by alessiadele on 2018-12-13
HI everyone!
When I power on my computer, the dual boot shows me both ubuntu and windows 10, but it loads just ubuntu: when I choose windows 10, a black mirror appears.

So I've tried to use the following command on ubuntu:

```
sudo fdisk -l

```
And the terminal shows me:

```
Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x6cede44d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 623128575 623126528 297.1G  7 HPFS/NTFS/exFAT
/dev/sda2       623130622 625129471   1998850   976M  5 Extended
/dev/sda3       625129472 937701737 312572266   149G 83 Linux
/dev/sda5       623130624 625129471   1998848   976M 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.
```


Now, how can I proceed? If I re-install windows, I can solve the problem?

---

### Post by ajgreeny on 2018-12-13
It will be more helpful to see exactly what the current situation is so see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by alessiadele on 2018-12-13
Well, I've followed the guide, and I've got this url:

[http://paste.ubuntu.com/p/8srk2BzZxX/](http://paste.ubuntu.com/p/8srk2BzZxX/)

I hope it's the right information you need!

---

### Post by yancek on 2018-12-13
Take a look at the instructions in post 5 and post 11 by oldfred at the link below.  You appear to have EasyBCD on windows.  You will likely need a windows install or repair CD/DVD to fix this.  You have the standard windows boot files on the windows partition and that partition is marked active which is correct.  The entry in grub.cfg for windows on sda1 is also correct so getting rid of EAsyBCD might work.  If you look at the output of boot repair under /dev/sda at the very top, you will see it is looking for the core.img file at a certain sector and it is not there.  

[https://ubuntuforums.org/showthread.php?t=2001733](https://ubuntuforums.org/showthread.php?t=2001733)

---

### Post by oldfred on 2018-12-13
Ignore partition 2 does not start on partition boundary.
Partition 2 is your extended partition and you do not write into it. It just is a container for all the logical partitions which you do write into and are ok.

Windows 10 in BIOS boot mode is not dual boot friendly. 
You must have Windows 10 fast start up off, but on updates Windows will turn it back on. And that sets hibernation flag so Ubuntu NTFS driver will not see it or see it read/write. And then grub will not boot Windows.
You need a Windows repair flash drive.

You may be able to temporarily restore a Windows type boot loader to MBR, and directly boot Windows. You may need to use f8 to get into its own internal repair console. You need to turn off fast start up and/or make other repairs. And make the Windows repair flash drive.
Then use Boot-Repair to restore a grub boot loader to MBR and grub should correctly offer to boot Windows.
Keep both the Windows repair flash drive & Ubuntu live installer so you can always make repairs as any Windows issue & grub will not boot it.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

