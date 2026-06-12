---
title: "grub.cfg - which one?"
date: 2016-08-29
forum: General Help
---

### Post by Geoff_Lane on 2016-08-29
Folks,

I am getting totally confused with grub configuration.

I have an old stable 12.04 on sda4, also 16.04 on sda6. Windows Vista on sda1 and 2 if I recall. I also used a liveUSB version to experiment with a USB stick installation.

Initially I had grub installed to SDA boot sector but I'm trying to change default boot but don't seem to work.

So I have grub.cfg on sda4, sda6 and my USB stick and have no idea which file is used.

I'm sure there is a grub command for this but can't fathom it.

Any pointers appreciated.

Geffers

---

### Post by Dennis N on 2016-08-29
Assuming this is a BIOS system, if you installed 16.04 most recently, and if you do nothing else, you would now be booting to that grub menu. To switch back to using 12.04, boot into the 12.04 OS and run:

```
sudo grub-install /dev/sda

```
then
```
sudo update-grub

```

---

### Post by grahammechanical on 2016-08-29
I assume that you only have one hard drive (sda). So, take your pick. Choose 12.04 or 16.04 and load into it and then run these two commands

```
sudo grub-install /dev/sda
sudo update-grub
```

If you do that from 16.04, then 16.04 will be in charge of the boot menu.

Regards.

---

### Post by oldos2er on 2016-08-31
Moved to General Help.

---

### Post by mook765 on 2016-08-31
Only one of the systems should have Grub installed in MBR. The second system doesn't need Grub anymore, but if installed then in it's own partition. If both sytems install Grub to MBR, both systems will control Grub in MBR.Whenever one of the systems runs update-grub(e.g. automaticly after kernel-upgrade) you would get scrambled configuration.
16.04 is on sda6.
12.04 is on sda4.
Install Grub from 16.04 to MBR(sda) and install Grub from 12.04 to sda4 (this is the better choice)
or
install Grub from 12.04 to MBR(sda) and install Grub from 16.04 to sda6
In the system which installs to MBR(sda)  you configure Grub.
Use the mentioned commands, but for one of the systems use "sudo grub-install sda**x**" (**x**=4 or **x**=6).

---

### Post by Keith_Helms on 2016-09-01
Whichever OS appears at the top of your boot menu is likely the one whose grub.cfg is actually being used.  I have 3 boot partitions with Xubuntu 14.04 and 2 copies of Xubuntu 16.04 in them.  Whenever an update to grub comes along on one of those systems, it appears grub-install gets invoked under the covers and that system ends up controlling the boot menu.  I then go into the 16.04 system that I want to control boot and manually run "sudo grub-install /dev/sda" in order to switch "ownership" of the MBR back.

---

### Post by mook765 on 2016-09-01
Keith_Helms, if you have three operating-systems and all off them have Grub installed in MBR, then all three systems "own" Grub in MBR.
The command "sudo grub-install /dev/sda" does not switch the "ownership". The other systems still "own" Grub as well. But after this command you will run "sudo update-grub" which will reorder the menu-entries.
Whenever one off the other systems runs update-grub later, your boot-menu will be changed again, because they still "own" Grub in MBR too, the system which was doing the update takes first place in the boot-menu. It is not that there will be another grub-install invoked. It is update-grub what changes the order menu-entries...
 It is better to have Grub installed in MBR only for one system, the other systems wouldn't need Grub then anymore, but if they have Grub installed, then on their own partitions. Unnecessary unless you want to create a chainload...

---

### Post by Bashing-om on 2016-09-01
Guys: et al;

My system:
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   102402438    51200195+  83  Linux
/dev/sdb2   *   102404096   204804095    51200000   83  Linux
/dev/sdb3       204806144   266246143    30720000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdc1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$

```

I manage my grub in a somewhat unorthodox manner - that I do understand and it works for my use case.
Bear in mind that there can be only one controlling authority for booting . Choose what you want as the primary booting system.
Now in my use case I have 5 'buntus installed on 2 hard drives.
My solution to control grub is that my primary - 1404mini:- controls grub, and I have also embedded grub for lubuntu to the sda7 partition !
As there can be only one bootloader in MBR .. one then turns off 30_os-prober in the directory /etc/grub.d/ ( sudo chmod -x /etc/grub.d/30_os-prober  ), update each install's grub to re-generate it's own config file, and finally update-grub in the primary to pick up and chainload all the other installs to it's boot menu .

[INDENT][INDENT]what works for me - I try to keep it simple
[/INDENT][/INDENT]

---

### Post by Keith_Helms on 2016-09-01
> **mook765 said:**
> Keith_Helms, if you have three operating-systems and all off them have Grub installed in MBR, then all three systems "own" Grub in MBR.
The command "sudo grub-install /dev/sda" does not switch the "ownership". The other systems still "own" Grub as well. But after this command you will run "sudo update-grub" which will reorder the menu-entries.
Whenever one off the other systems runs update-grub later, your boot-menu will be changed again, because they still "own" Grub in MBR too, the system which was doing the update takes first place in the boot-menu. It is not that there will be another grub-install invoked. It is update-grub what changes the order menu-entries...
 It is better to have Grub installed in MBR only for one system, the other systems wouldn't need Grub then anymore, but if they have Grub installed, then on their own partitions. Unnecessary unless you want to create a chainload...

Whatever terminology you want to use, it appears the MBR/boot process is only pulling in the grub.cfg file from a single boot partition at a time.  Let's say the MBR "points" to sda1.  If I boot the OS in sda2, run software updater and it installs a new kernel version, the grub.cfg in the sda2 partition will be rebuilt and that kernel version will be listed under its advanced options.  However, that new kernel version will **not** be listed when I reboot the system because the MBR is pulling in grub.cfg from sda1, not sda2.  I have to run update-grub when booted into the sda1 OS in order to pick up the newest kernels installed in the sda2 OS.

I have also observed that whatever partition/OS I last ran "sudo grub-install /dev/sda" in is the one whose grub.cfg is referenced at boot time.

---

### Post by mook765 on 2016-09-01
Keith_Helms, I agree 100%. You just brought it on the spot...

---

### Post by Geoff_Lane on 2016-09-02
Folks,

Thanks for all the replies, I thought I subscribed to this thread but somehow didn't so wasn't notified of replies.

Understand a bit more now.

Strangely, on a similar 'booting' subject; bought new laptop with Win10 installed (Yuk), the preserve warranty am running my old Ubuntu systems from an external enclosure, whilst playing about with GRUB my UEFI on new computer has disappeared and I need external enclosure attached to boot into Win10 - which I seldom do.

Anyone know how to reinstall the UEFI system on new laptop?

Geffers

---

