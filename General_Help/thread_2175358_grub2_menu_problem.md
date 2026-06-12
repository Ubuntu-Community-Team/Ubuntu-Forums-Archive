---
title: "grub2 menu problem"
date: 2013-09-18
forum: General Help
---

### Post by dgundling on 2013-09-18
I had Ubuntu 12.04, 12.10, and 13.04 installed each would boot. The Grub menu for the 12.10 and 13.04 versions was a mess. Downloaded and tried to correct the problem with Grub Customizer without success.

Next I booted to 12.04 and deleted 12.10 and 13.04 using the disk utility in 12.04. Next I deleted the partitions they were loaded on entirely using the disk utility in 12.04. Got into the terminal and ran sudo update-grub. Closed the terminal and shut down 12.04. I rebooted and the grub boot menu was had not changed. What did I do wrong? How should I go about it? Is it possible?

---

### Post by ankspo71 on 2013-09-18
I don't have any advice for Grub Customizer, sorry.

As for the second problem, I'm pretty sure you tried to only run "update-grub" on a version of Ubuntu that didn't have its grub2 configuration installed to the MBR anymore (because of the MBR being overwritten by 12.10's or 13.04's grub). If that was the case, then the following commands should have helped:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
``` Searches for other os'es and generates a new grub configuration file accordingly.
```
sudo grub-install /dev/sda
``` Installs grub2 configuration to the MBR of the first drive.
```
sudo update-grub
``` Adds any user changes in /etc/default/grub to the configuration.

A great tool for grub2 fixes and diagnostics is Ubuntu Boot Repair. The second option on the following link allows us to use this tool on an Ubuntu live cd.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I haven't tried it for grub2 menu cleanup and it's been a while since I used it though.

---

### Post by dgundling on 2013-09-20
Ankspo71,

Thanks for the reply. The delay in my getting back to you was due to inability to log in when using the link to your response.
The log in screen was partially blocked and I was unable to enter the fact that I have an account or my password. Don't know how to report the problem.

Tried your suggestion and it did not work for me. I did manage to render the computer unbootable. I tried boot repair and apparently deleted grub entirely. I assumed when the warnig screen came up that grub would be deleted and and then the compuiter would regenerate a new one. No go. Now I need to find out how to use grub rescue. I can always try an installation disk and wipe the hard drives entirely but that is, as you know, extremely time consuming.

---

### Post by oldfred on 2013-09-21
For Boot-Repair to reinstall grub2, you have to have a working network connection so it can download the grub files to reinstall. Was network working?


Another alternative, but if you have uninstalled grub, it may not find menu to boot.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by dgundling on 2013-09-21
Old Fred,

Thanks for the reply.

The network was working when I was using Boot Repair. Now. since the computer won't boot, I don't have a working network connection. This reply was generated on another computer.

Need to find out more about super grub disk. When I followed your link, the resulting page allowed a download but provided little info on it. I am unfamiliar with "UEFI" will need to check it out also.

---

### Post by oldfred on 2013-09-21
I do not know if Supergrub has been updated to work with UEFI. 
It is just a simple grub boot that scans system like os-prober and creates boot entries. Then from within your booted system you can make repairs. That is often easier than a chroot into your system and repairs.

---

### Post by dgundling on 2013-09-28
Still have a problem with grub rescue. I have tried Boot Repair without success. I have two hard disks installed. I had 12.04 on sda and 13.04 on sdb. After failing to make progress, I decided to just reinstall. The only live disk that I had that would actually work was the 13.04 disk. During the install process I wiped the sdb disk partitions clean and did the reinstall to the same partition that held 13.04 before. The machine said that installation was complete, but upon reboot I was back to grub rescue again. Next I tried installing 13.04 on sda. I created a new partition for it and went through the installation process. Again the machine reported installation complete but I got grub rescue again on reboot. Do I need to completely wipe both hard disks and start again? How do I get rid of  grub rescue and get a boot menu again? Thanks for any help.

---

### Post by Bashing-om on 2013-09-28
dgundling; Hi !
Dealing with grub can be a daunting process.

Is it 13,04 on sdb that you want as the primary booting operating system ?
If so ..try this:
Set in bios to boot that 2nd drive as the 1st boot priority;
You will need a LiveCD/USB. Boot into the Live Environment and Activate a Terminal;
You need to know the partitioning of the hard disk, where the boot code is located (the "*" character);
```

sudo fdisk -l

```
for this instruction I am going to "assume" a standard install having that boot code located in the two standard places ..
the MBR (master Boot Record) SDB
and the final boot code is at SDB1. You do NOT have a separate /boot set up !

Mount your OS partition:
```

sudo mount /dev/sdb1 /mnt

```
Next, install GRUB2 to where it needs to be in this scenerio;
```
sudo grub-install --boot-directory=/mnt /dev/sdb
##(Don't put a partition number in this command, just the HDD location that is the primary boot; a, b, etc.)

```
Now unmount:
```

sudo umount /mnt

```
Now let's see what you got ! Reboot, removing the liveDVD,
booting the sdb hard drive (you set that in bios, right ?)
```

sudo shutdown -r now

```

Hey, it is just a process, bios must know where the boot code is and hands off to that location, and the boot code must be there.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by dgundling on 2013-09-29
Bashing-om,

Thanks for the reply. Tried your suggestion but it didn't work. The sudo fdisk -l command workes and it showed that I had boot code on both sda and sdb. Since the last operation that I pderofrmed was to try to reinstall 13.04 on sda. I modified your suggested commands to use sda instead of sdb on my first attempt. Got an error after the grub-install command. Tried again using the commands as you gave them to me. Again got an error at the grub-install command.

Back to the drawing board.

---

### Post by Bashing-om on 2013-09-29
dgundling;

It has to work if ;
a) You set the bios boot priority to a drive that has Grub installed,
b) Grub is installed onto the MBR that you are pointing bios boot priority to,
c) The install command's paths are in accordance with the "fdisk" output.
else:
We are talking about advanced booting methods, as in UEFI and/or secure boot;
advanced partitioning schemes that require a separate /boot partition (GPT).

Post back to us the output of
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```

as well as the command that you will use to install grub.

[INDENT]it is a process that just works
[/INDENT]

---

### Post by dgundling on 2013-10-05
Bashing on,

Here is the output you requested. Sorry for the delay in responding. Got tied up last week.

dave@dave-MS-7125:~$ sudo fdisk -lu
[sudo] password for dave: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcec5cf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20482047    10240000   83  Linux
/dev/sda2        20482936    53989610    16753337+   f  W95 Ext'd (LBA)
/dev/sda5        20482938    24691904     2104483+  82  Linux swap / Solaris
/dev/sda6        24692736    53989610    14648437+  83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046155

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    29296969    14647461   83  Linux
dave@dave-MS-7125:~$ sudo parted -l
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.5GB  10.5GB  primary   ext4            boot
 2      10.5GB  27.6GB  17.2GB  extended                  lba
 5      10.5GB  12.6GB  2155MB  logical   linux-swap(v1)
 6      12.6GB  27.6GB  15.0GB  logical   ext4


Model: ATA Maxtor 6L200P0 (scsi)
Disk /dev/sdb: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.0GB  15.0GB  primary  ext4         boot


dave@dave-MS-7125:~$ sudo parted /dev/sda unit s print
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End        Size       Type      File system     Flags
 1      2048s      20482047s  20480000s  primary   ext4            boot
 2      20482936s  53989610s  33506675s  extended                  lba
 5      20482938s  24691904s  4208967s   logical   linux-swap(v1)
 6      24692736s  53989610s  29296875s  logical   ext4

dave@dave-MS-7125:~$ sudo parted /dev/sdb unit s pring
Usage: parted [OPTION]... [DEVICE [COMMAND [PARAMETERS]...]...]
Apply COMMANDs with PARAMETERS to DEVICE.  If no COMMAND(s) are given, run in
interactive mode.

OPTIONs:
  -h, --help                      displays this help message
  -l, --list                      lists partition layout on all block devices
  -m, --machine                   displays machine parseable output
  -s, --script                    never prompts for user intervention
  -v, --version                   displays the version
  -a, --align=[none|cyl|min|opt]  alignment for new partitions

COMMANDs:
  align-check TYPE N                        check partition N for TYPE(min|opt)
        alignment
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on
        COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition
        table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partition NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START
        and END
  resize NUMBER START END                  resize partition NUMBER and its file
        system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
        NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and
        copyright information of GNU Parted

Report bugs to [email]bug-parted@gnu.org[/email]
dave@dave-MS-7125:~$ t
t: command not found
dave@dave-MS-7125:~$ sudo parted /dev/sdb unit s print
Model: ATA Maxtor 6L200P0 (scsi)
Disk /dev/sdb: 398297088s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      2048s  29296969s  29294922s  primary  ext4         boot

I don't have a command to install grub. Grub, for me, is installed when I install the Ubuntu distro from a live disk.

---

### Post by Bashing-om on 2013-10-05
dgundling; Hey !

Not a problem in your getting back in a timely manner .. live interferes !

OK, I see no reason to this time that we can not install grub onto the 1st hard drive sda.
With this RESERVATION -> sda2 is a Windows extended partition, with a ubuntu swap (sda5) partition inside this extended partition as a logical partition. Not sure at all how this could work out !
Let's look a bit deeper. 
Boot the liveDVD -> try ubuntu mode -> ctl+alt+t yields a terminal >
Terminal codes:
```

sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test
ls -la /mnt/test/home/dave
cat /mnt/test/etc/fstab
ls -la /mnt/test/boot

```
Where "dave" is the user name you applied when you installed onto sda; else use the correct username you installed with.

When the above is completed and you are done looking around - most important ! -> UNmount the device sda1 !
```

sudo umount /mnt/test

```

Looking for a reason that grub does not install and a means to make grub install onto sda. We look to want to boot ubuntu from the sda1 partition.

Next, at some point, we will want to look at the sda6 partition ... and as to sdb (2nd hard drive) - single partition only dedicated to linux - I do not care about it if you do not have a concern.

[INDENT][INDENT]we just look'n to see [/INDENT][/INDENT]

---

### Post by dgundling on 2013-10-06
Bashing-om,

Found the cause of the bulk of my problems. The BIOS battery was all but dead. Replaced it and all is acting normal. Even the grub menu looks OK. Thanks for your help. I learned some things from your efforts. BTW, do you know of a good reference for terminal commands? Thanks again.

Dave

---

### Post by Bashing-om on 2013-10-07
dgundling; Well , well well ;

Not at all the first time dead/weak bios battery has made it presence known ! 5yrs=replace battery ! huh ?

If this issue is concluded, please mark this thread as solved. This aides others seeking solutions and helps keep the forum tidy.
 
" BTW, do you know of a good reference for terminal commands? Thanks again."
That is a Very broad category. Start with the "sticky" in the beginners' forum, then spend lots of time with "NewDocs" linked in my sig. Thank BlinknCat - and support personnel - for all the hard work !
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

[INDENT][INDENT]who wudda thunk it
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-10-07
Some more information.

 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

---

### Post by dgundling on 2013-10-07
Bashing-om,

I looked all over this thread page after posting about the battery and never found a means to mark it as problem solved. I finally just entered problem solved in the tags area. Where does one mark a thread as solved?

Thanks.

---

### Post by Bashing-om on 2013-10-07
dgundling; Hey,

In order to mark the thread as "solved" go to YOUR 1st post if you are the original poster, and the tool is in the "thread tools" link at the top right of the post.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

