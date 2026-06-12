---
title: "shutdown ubuntu and chainload windows"
date: 2016-12-04
forum: General Help
---

### Post by garlorsus on 2016-12-04
is there any way possible to shutdown your ubuntu/linux and boot windows?, without rebooting the machine/going through grub

basically I wanna check by lan what OS needs to be booted on a machine, this can't be done with grub, and pxe management is out of my hands, is there any way I can boot up a minimal ubuntu check what partition I want booted and then close itself and load/chainload that partition's OS?

---

### Post by kingneutron on 2016-12-05
--It would really help if you stated WHY you need to do this remotely... And how often it would need to be done.

--I can think of a couple of hacks to do this, but they both involve rebooting.

--If you install the "mbr" package and read the man page " man install-mbr " you can set it to boot from whatever partition has the "active" flag:
```

       -p <partn>, --partition <partn>
              This specifies the default boot sector to load.  Valid values of <partn> are:

              1, 2, 3, 4
                     The specified partition number.

              F      The first floppy disk.

              D      The partition marked with the bootable flag in the partition table.

```

--The other method involves messing around with grub config, which I suspect you don't want to get into.

--If you end up going with mbr, this would be how you would invoke the command:
```

sudo install-mbr -v -p D /dev/sdX

```

--Obviously, replace sdX with whatever drive you are using.  After that, you can invoke 
```

sudo fdisk /dev/sdX 

```

...and hit "p" to print partitions, "a" to set the Active flag on a partition, "w" to write the changes to disk, and "q" to quit.

--Note that this can only be done remotely from Linux, AFAIK. If you set the active partition and boot to Windows, you'd pretty much need to be at the machine to boot System Rescue CD or something to redo the above steps to get it back booting to Linux.

```

root ~ # fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   197267672    98632812+  17  Hidden HPFS/NTFS
/dev/sda2   *   197267673   246093823    24413075+  83  Linux
/dev/sda3       246095798   294922239    24413221   83  Linux
/dev/sda4       294923923  1953525167   829300622+   5  Extended
/dev/sda5       294925971   296925970     1000000   82  Linux swap / Solaris
/dev/sda6       296929280   545419263   124244992    7  HPFS/NTFS/exFAT
/dev/sda7       545421312   567951359    11265024    b  W95 FAT32
/dev/sda8       567953408   695427071    63736832    7  HPFS/NTFS/exFAT
/dev/sda9       695429120  1953523711   629047296   83  Linux

Command (m for help): a
Partition number (1-9): 2

```

--You may be able to (re)set the active partition from Windows, which should then boot Linux/grub when the machine is restarted, but I cannot guarantee anything:
[http://superuser.com/questions/596919/how-to-set-boot-disk-flag-with-diskpart](http://superuser.com/questions/596919/how-to-set-boot-disk-flag-with-diskpart)

--PLEASE NOTE that this is theoretical on my part, I take no responsibility if you damage your system or become unable to boot, recommend trying this in a VM first, and **be sure you have good backups **before you go playing with OS boot sequences on your machine.  **Also, go download a copy of "super grub disk" and burn the ISO to CD in case things go awry.** It can autodetect operating systems and boot them without a working grub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

--Alternative/Advanced concept: You could "burn" System Rescue CD to (2) different USB sticks, and have an "autorun" script to change the partition flag depending on which one you boot. 
[https://www.system-rescue-cd.org/Sysresccd-manual-en_Run_your_own_scripts_with_autorun](https://www.system-rescue-cd.org/Sysresccd-manual-en_Run_your_own_scripts_with_autorun)

---

### Post by oldfred on 2016-12-05
If UEFI you can set the UEFI one time reboot key to boot a system that is not the default.
see this and boot next command parameter:
man efibootmgr

---

