---
title: "vista boot,dual boot"
date: 2012-12-19
forum: General Help
---

### Post by skudder on 2012-12-19
hello. 
I have a problem with vista on another drive. I liked unbuntu  and i had it on a pen drive.
I decided to install it on a drive of two, one had vista and the other had xp . when i was using pendrive linux I decided to install onto the drive d: that had xp ,because I never used it that much .I cannot boot into my vista c: drive anymore after installing.I had my vista 64 cd ready to do a rescue.but when i set my bios to boot from my dvd, my dvd wont boot for some reason. 
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   304193535   152095744   83  Linux
/dev/sda2       304195582   312580095     4192257    5  Extended
/dev/sda5       304195584   312580095     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   304193535   152095744   83  Linux
/dev/sdb2       304195582   312580095     4192257    5  Extended
/dev/sdb5       304195584   312580095     4192256   82  Linux swap / Solaris
clayton@clayton-desktop:~$

---

### Post by oldfred on 2012-12-20
Did you install XP, then install Vista? Second installs of Windows often put its boot files in the first install as the is the drive in BIOS and the partition with the boot flag or active partition.

To see what is where. This will not fix Windows issues but will hopefully show what may be missing.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

    
How Windows multi-boots
       Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by skudder on 2012-12-20
Not sure which i installed first.
[http://paste.ubuntu.com/1451701/](http://paste.ubuntu.com/1451701/)

---

### Post by oldfred on 2012-12-20
You are only showing the flash drive as sdb & the RAID in sda & sdc? 

You only show Ubuntu installed in a nvidia RAID system. That is BIOS raid which has limited advantages and is also know as fakeRAID.
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

Did you turn RAID on in BIOS and then install to the entire drive overwriting the entire old systems?

---

### Post by skudder on 2012-12-20
I may have turned it on in bios long ago when it was my first time installing two hard drives.I did set bios to default in a  attemp before posting to recover vista. Do you recomendd turning raid off and reinstalling everthing?Its all a bit complicated to me
thankyou,

---

### Post by oldfred on 2012-12-20
I am not a fan of RAID on most desktops, so my suggestion is to reinstall. And I prefer to have Windows totally installed to one drive so it can boot without the other drive and Ubuntu totally installed to the other drive so it can boot without the Windows drive. Data partitions then can be on either or both drives and if NTFS used by both systems.

 Many suggest unplugging drives to be sure they are installed separately. The main issue is often where the boot loader files get installed. And if you set Ubuntu drive as second drive but boot drive from BIOS you can run this and boot either Ubuntu or Windows.
sudo update-grub

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
    
       Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

RAID leaves meta-data on drives which must be removed before install. IF sdc change example below.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

