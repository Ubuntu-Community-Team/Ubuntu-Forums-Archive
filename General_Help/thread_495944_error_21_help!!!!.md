---
title: "error 21 help!!!!"
date: 2007-07-08
forum: General Help
---

### Post by samee on 2007-07-08
i have just installed ubuntu on my partitioned hdd.

the hdd is partitioned into four segments/parts as follows:
1 for windows vista, another for data, one for ubuntu 7.04, a swap section for ubuntu. 
after successfully coimpleting the installation i recieve the following error message after rebooting 

GRUB Loading stage 1.5


GRUB Loading please wait...
Error 21.

i cant even boot in vista 

what might be the problem?

---

### Post by confused57 on 2007-07-08
> **samee said:**
> i have just installed ubuntu on my partitioned hdd.

the hdd is partitioned into four segments/parts as follows:
1 for windows vista, another for data, one for ubuntu 7.04, a swap section for ubuntu. 
after successfully coimpleting the installation i recieve the following error message after rebooting 

GRUB Loading stage 1.5


GRUB Loading please wait...
Error 21.

i cant even boot in vista 

what might be the problem?
From the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You might want to read over this description of error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by samee on 2007-07-09
after entering *sudo fdisk -l* in the terminal the results are as follows:

To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.



ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/hda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

  
 
   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1        2597    20858880    7  HPFS/NTFS

/dev/hda2            2597        8138    44502016    7  HPFS/NTFS

/dev/hda3            8138        8399     2096128+   f  W95 Ext'd (LBA)

/dev/hda4            8399        9730    10690560   83  Linux

/dev/hda5            8138        8399     2096128   82  Linux swap / Solaris

ubuntu@ubuntu:~$ 

hope this helps reply asap. thanks

---

### Post by fredj on 2007-07-09
Where is that extra W95 partition coming from. You said you only had 4 partitions.
Boot into ubuntu open a terminal and cd to /boot/grub. Type sudo gedit menu.lst and see which partition
grub is using to boot unbuntu. Then think about whether that extra W95 partiton is getting in the way.

---

### Post by samee on 2007-07-10
after typing *sudo gedit menu.lst* it opens a new window and says noting in the white space. in the title menu it says the following; menu.lst (/home/ubuntu) - gedit.

i have opened GNOME partition editor and took a screenshot if it helps.

---

### Post by samee on 2007-07-10
i have just started to use ubuntu and may not know a lot of the OS so please explain in some detail thanks sam.

---

### Post by Bothered on 2007-07-10
The fdisk output and gparted output don't seem to match up. However, it looks (from gparted) like the linux partition is not marked as bootable. Try enabling the boot flag on /dev/hda4.

EDIT: You'll probably need to unmount it first. Use "sudo umount -a" to unmount all drives.

---

### Post by samee on 2007-07-10
i have made the /dev/hda4 part bootable and says boot under the flag column when i try restarting the computer i recieve the same error message:
GRUB Loading stage 1.5


GRUB Loading please wait...
Error 21.

thanks for the quick response

---

### Post by hooksie on 2007-07-10
> **fredj said:**
> Where is that extra W95 partition coming from. You said you only had 4 partitions.
Boot into ubuntu open a terminal and cd to /boot/grub. Type sudo gedit menu.lst and see which partition
grub is using to boot unbuntu. Then think about whether that extra W95 partiton is getting in the way.

It's the extended partition, which is broken up into the other 3 partitions from there.

---

### Post by samee on 2007-07-10
how can i resolve the extended partition issue????

---

### Post by samee on 2007-07-10
i dont know what the w95 partition is but it does NOT appear in computer

---

### Post by samee on 2007-07-10
if i remove the ubuntu files from the two partitions also remove the two partitions will i be able to boot back to windows vista?

---

### Post by Bothered on 2007-07-10
Unfortunately no, as the ubuntu installer has overwritten the Windows master boot record.

EDIT: I believe the ms-sys package can be used to fix this from the ubuntu Live CD, although I have never done this myself.

---

### Post by dabl on 2007-07-10
Windows Vista now requires 2 partitions minimum -- those are your first 2.  The little "unallocated space" is probably what you accidentally left when you made new partitions - it is presently wasted space.

If it were me, I would use a GParted Live CD to delete (combine) the last 3 partitions plus that unallocated space, and then try again (while leaving the Vista partitions alone).  I would make a 1GB primary partition for swap, and then the rest of it I would use for an extended partition, and in that one I would put two logical partitions, one of 8GB for "/" and the rest of the available space for "/home".

GParted Live CD ISO image comes from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then you will need to boot the Windows recovery disk and use one of the "fixmbr" family of commands to straighten out the boot block.  Search on it -- there are many posts on that topic.

Hope this helps! :)

---

### Post by samee on 2007-07-10
how can i resolve the extended partition problem

---

### Post by confused57 on 2007-07-10
> **samee said:**
> if i remove the ubuntu files from the two partitions also remove the two partitions will i be able to boot back to windows vista?
If it were me, I would try reinstalling Ubuntu...I noticed in your gparted attachment that the mountpoint for /dev/hda4 was /media/disk...this should be mountpoint /, for your root partition.  You should be able to select manual partitioning and make sure to select the mountpoint as /, format as ext3, primary partition...and your swap on /dev/hda5, mountpoint swap, format as swap, logical partition.

dabl made an excellent suggestion, even a better idea:
> If it were me, I would use a GParted Live CD to delete (combine) the last 3 partitions plus that unallocated space, and then try again (while leaving the Vista partitions alone). I would make a 1GB primary partition for swap, and then the rest of it I would use for an extended partition, and in that one I would put two logical partitions, one of 8GB for "/" and the rest of the available space for "/home".

---

### Post by samee on 2007-07-10
> **confused57 said:**
> If it were me, I would try reinstalling Ubuntu...I noticed in your gparted attachment that the mountpoint for /dev/hda4 was /media/disk...this should be mountpoint /, for your root partition. 

you have said mount point / does this mean where it says mount point and has an empty box do i type / in th box or not 

and is that the same wit the swap mount point tor not?

---

### Post by confused57 on 2007-07-10
> **samee said:**
> you have said mount point / does this mean where it says mount point and has an empty box do i type / in th box or not 

and is that the same wit the swap mount point tor not?
You'll probably need to reinstall, but you can try changing the mountpoint to /...you'll need to mount your /dev/hda4, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

change the mountpoint of /dev/hda4 in fstab from /media/device to /...quit & save...If fstab already has the mountpoint as / for /dev/hda4, I'm not sure what's going on...if it does, you might want to post your /boot/grub/menu.lst and /etc/fstab.

---

### Post by samee on 2007-07-10
UPDATE!!

i have removed the three partitions and now have 2 partitions i have used gnome partition editor. see screen shot for more info

now can u tell me step by step how to install Ubuntu via the live cd including partitions mount point type etc. thanks in advance. sam

---

### Post by samee on 2007-07-10
after removing the partitions and not touching the vista partitions i have then partitioned the HDD in for 1GB swap section the rest has been set for extended partition and in the extended partition 2 sub partitions 1 partition with a mount point / and onother with a mount point /home.
and..... still not able to boot with the same error message:

GRUB loading stage 1.5


GRUB loading, please wait...
Error 21.

---

### Post by confused57 on 2007-07-10
> **samee said:**
> after removing the partitions and not touching the vista partitions i have then partitioned the HDD in for 1GB swap section the rest has been set for extended partition and in the extended partition 2 sub partitions 1 partition with a mount point / and onother with a mount point /home.
and..... still not able to boot with the same error message:

GRUB loading stage 1.5


GRUB loading, please wait...
Error 21.
Grub error 21 on a single dual boot hard drive is rare and is usually a "bug" associated with the chipset controllers and Ubuntu...you could try going into your bios setup and maybe try a different setting for your hard drive controller...only make one change at a time and write down what you change so you can change it back...a search showed setting the master hard drive controller to Type=User & Mode=LBA worked for one person.

You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see if SGD can boot your Vista or Ubuntu

Also, you might want to boot the live cd and post the output of:
```
lspci
```
this will show your hardware & what "may" be causing the problem.  While you're booted to the live cd, check the output of:
```
sudo grub
find /boot/grub/stage1
quit
```

If SGD or changing bios settings don't work, there are some other things you could try:
1.) Use the alternate cd & use lilo as the bootloader:
[http://users.bigpond.net.au/hermanzone/p4.html#Lilo_alternate_install](http://users.bigpond.net.au/hermanzone/p4.html#Lilo_alternate_install)

2.) Install grub to the root partition and try using the GAG bootloader(floppy or cd):
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

Are you using gparted on the live cd installer to format your partitions?  I'm asking this because using Window's based partitioning tools to format ext3 can cause problems.

I would recommend trying Super Grub Disk first...post the output of the 2 commands above and you might want to post:
```
sudo fdisk -l
```

then mount your root partition, then post your /boot/grub/menu.lst and /etc/fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If SGD doesn't work and the output of the commands I've mentioned don't really reveal the problem, then you might try lilo or GAG.

Added:  Just found this thread that used a combination of lilo and GAG to set up their dual boot:
[http://ubuntuforums.org/showthread.php?t=498085](http://ubuntuforums.org/showthread.php?t=498085)

---

### Post by samee on 2007-07-11
the output of lspci is as follows;'

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
]

the output for sudo grub etc is as follows:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 
 (hd0,4)

grub> 


and how do i make Super Grub Disk: boot my pc?
i will also try changing the BISO as you have requested i will reply as i get the results.

---

### Post by samee on 2007-07-11
some good news at last after chnagng the BIOS settings i was able to boot from ubuntu vis the HD. :) and also gave me an option for other os like vista i will try to boot from vista and get back asap .

---

### Post by samee on 2007-07-11
ok vista and ubuntu both boot finally from the hdd.

i also made one partition /boot by editing it and then also chnaging the biso setting also and then dual booting worked.

thanks for all your help sam.

---

### Post by confused57 on 2007-07-11
> **samee said:**
> ok vista and ubuntu both boot finally from the hdd.

i also made one partition /boot by editing it and then also chnaging the biso setting also and then dual booting worked.

thanks for all your help sam.
Good job...glad it worked & was just a bios setting issue.

---

