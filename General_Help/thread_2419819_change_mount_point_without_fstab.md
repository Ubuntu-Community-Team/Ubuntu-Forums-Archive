---
title: "change mount point without fstab"
date: 2019-05-25
forum: General Help
---

### Post by linux.girl on 2019-05-25
Hello friends,

I have the latest version of Ubuntu.

I want to change the mount point of my external USB disk without putting an entry on fstab - I want it to automatically mount on media. I have been looking around, but I am seeing only fstab options and this is not healthy for external drives. Any suggestions?

Another question: I have an internal SATA disk (second) that I want to use as storage - but Ubuntu is not seeing it so I cannot mount - any suggestions how to make it see the second internal disk?

Thanks!

---

### Post by oldfred on 2019-05-25
Partitions on your external drive should automount, if  you click on them in Naulitus, or whatever file browser you use.

Do you have partitions on your internal drive, what format?
You generally have to create a mount point, mount partition and give yourself ownership & permissions to use it.

I normally follow these directions by Morbius1.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

I typically mount data partition where not normally seen & then link folders into /home. But you can mount directly into /home if desired.
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by sisco311 on 2019-05-25
You can create a udev rule to mount all removable drives under /media, see: [https://wiki.archlinux.org/index.php/Udisks#Mount_to_/media_(udisks2)]("https://wiki.archlinux.org/index.php/Udisks#Mount_to_/media_(udisks2)")

If you wish to mount only one specific drive to /media then you will have to create a more specific udev rule.

> **linux.girl said:**
> 
Another question: I have an internal SATA disk (second) that I want to use as storage - but Ubuntu is not seeing it so I cannot mount - any suggestions how to make it see the second internal disk?

What's the output of:
```
sudo fdisk -l
sudo blkid
```
?

---

### Post by SeijiSensei on 2019-05-26
I have an [external USB drive]("https://www.newegg.com/p/N82E16822178745") that I use for backups. It's connected all the time to my server and mounts at boot via /etc/fstab.  I write hundreds  of megaytes to it every night, and delete roughly the same amount of existing data, with no problems whatsoever.  Maybe your concern makes sense for external SSD drives. For externals with SATA drives installed, I doubt there is an issue.

---

### Post by linux.girl on 2019-05-28
Dear Friends, sorry for the late reply, I caught a bad virus and I also  didn't get a mail notification that anyone answered. So here are a few  developments since I last wrote. I managed to move the mount point to  /media/myusername/MyPassport5 - BUT - a few very weird things happened:

1 - A folder named MyPassport5 appeared under /media (not /media/myusername)
2  - Two other folders appeared under /media/myusername: MyPassport5 and  MyPassport51 - I have no idea where this 51 came from and it doesn't let  me delete and/or change anything so that I end up with only ONE folder  called /media/myusername/MyPassport5
3 - Regarding the internal media  - I haven't used it in ages, I don't know what's in there (filesystem,  etc) because I simply cannot see it on my Ubuntu anywhere, if I did, I  would format it and create a mount point, but I can't find it :-(

Any ideas what happened? Seems like a ghost took over my PC....

Thanks in advance!!!!!!!!!!!!!!

Here are the results of the commands you asked for - I tried to attach it in a text file but it didn't allow me saying the file was invalid.

```
x@linux:~$ sudo fdisk -l

Disk /dev/loop0: 93.6 MiB, 98168832 bytes, 191736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 53.7 MiB, 56328192 bytes, 110016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 53.7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 14.4 MiB, 15060992 bytes, 29416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 93.7 MiB, 98242560 bytes, 191880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 154.4 MiB, 161939456 bytes, 316288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.7 TiB, 4000786153472 bytes, 7814035456 sectors
Disk model: My Book 25DA    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 41E1B129-48BB-4D53-A5B9-7C27827C4F61

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 7814033407 7814031360  3.7T Microsoft basic data


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: SAMSUNG HD103SJ 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x60b1b719

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1  *     2048 1953523711 1953521664 931.5G 8e Linux LVM




Disk /dev/mapper/ubuntu--vg-root: 930.4 GiB, 998974160896 bytes, 1951121408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 89.3 MiB, 93581312 bytes, 182776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 34.8 MiB, 36503552 bytes, 71296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 35.3 MiB, 37027840 bytes, 72320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 3.7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 151 MiB, 158343168 bytes, 309264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 45.2 MiB, 47382528 bytes, 92544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 154.4 MiB, 161935360 bytes, 316280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 53.7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 151 MiB, 158347264 bytes, 309272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 3.7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 86.7 MiB, 90906624 bytes, 177552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 14.4 MiB, 15065088 bytes, 29424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 93.7 MiB, 98222080 bytes, 191840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 57 MiB, 59719680 bytes, 116640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 14.4 MiB, 15065088 bytes, 29424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 46 MiB, 48230400 bytes, 94200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 45.3 MiB, 47484928 bytes, 92744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 88.4 MiB, 92733440 bytes, 181120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 151 MiB, 158343168 bytes, 309264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 56.9 MiB, 59662336 bytes, 116528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 4 MiB, 4214784 bytes, 8232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 57 MiB, 59703296 bytes, 116608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 14.8 MiB, 15458304 bytes, 30192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 3.7 MiB, 3846144 bytes, 7512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 14.8 MiB, 15458304 bytes, 30192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 89.4 MiB, 93720576 bytes, 183048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdc: 3.7 TiB, 4000752599040 bytes, 7813969920 sectors
Disk model: My Passport 25E2
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7385FE26-33CB-46AD-9D49-3DC12577787C

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7813967871 7813965824  3.7T Microsoft basic data
```
```
x@linux:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="MyBook4" UUID="572685E54E62EBAD" TYPE="ntfs" PTTYPE="atari" PARTLABEL="My Book" PARTUUID="13a49276-3b33-4195-88f1-371266e4aafe"
/dev/sdb1: UUID="mdiFr9-iUd6-TbAV-uKg0-YmIB-oxLX-a1BJXV" TYPE="LVM2_member" PARTUUID="60b1b719-01"
/dev/mapper/ubuntu--vg-root: UUID="28d2bc97-d242-4f01-9a9b-6fddbc998346" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="78d56cc3-0fdd-4fde-bf38-90f3f3151a2a" TYPE="swap"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop32: TYPE="squashfs"
/dev/loop33: TYPE="squashfs"
/dev/loop34: TYPE="squashfs"
/dev/loop35: TYPE="squashfs"
/dev/loop36: TYPE="squashfs"
/dev/loop37: TYPE="squashfs"
/dev/loop38: TYPE="squashfs"
/dev/loop39: TYPE="squashfs"
/dev/loop40: TYPE="squashfs"
/dev/loop41: TYPE="squashfs"
/dev/sdc1: LABEL="MyPassport5" UUID="D22EE5202EE4FE7B" TYPE="ntfs" PARTLABEL="MyPassport5" PARTUUID="8f87b698-c199-4585-93f0-a593ab9e5686"
```

---

### Post by linux.girl on 2019-05-28
I took a screenshot so you can see more clearer.

Why the 51?

And why I don't see the internal disk? The tutorial by Morbius1 is in case I can find the disk - but I can't :-(

---

### Post by oldfred on 2019-05-28
You have used the advanced LVM - logical volume (and maybe encryption?) install.
It shows as sdb1 LVM.

If you unplug & then replug in an external device it often makes another entry in Naulitus side panel with the extra 1 at the end. Only one is valid and works.

You have an awful lot of loop devices, normally from installing snap type software, not standard software.
There are advantages & disadvantages to snaps.
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

I remove all snaps and only use  standard .debs installed. I use synaptic or command line. I think Ubuntu Software must now use snap as default?

You can exclude snaps in various listings of drives.
exclude snaps
lsblk -af |grep -sv loop
df | egrep -v /dev/loop
lsblk -e7 -f
df -h -x squashfs

---

### Post by linux.girl on 2019-05-28
Hi oldfred, first of all, thank you so much for the quick reply!

Indeed I used LVM (re "advanced" I don't know, I used the regular LVM option), but no encryption. I noticed the annoying loops - I did not install anything that did not come from official ubuntu and found out that they are using snaps by default - I don't understand why. Do you? Security perhaps? Microservices? If it is for security, not sure I want to disable the snaps.

"[COLOR=#000000]If you unplug & then replug in an external device it often makes another entry in Naulitus side panel with the extra 1 at the end. Only one is valid and works." - Why did they do that?? It is *so* annoying! I don't understand the purpose! It is the same external drive that I plugged and unplugged, why "trash" my PC with folders I don't need? I don't see the reasoning behind that, if someone can explain to me I would be very grateful. Is there a work around it?

How about the internal hard drive? Any ideas how can I "catch" it and format it when the OS is not seeing it?

Thanks!!!!!!!!!!!


[/COLOR]

---

### Post by oldfred on 2019-05-28
If you read the links on loops you will understand more about them. They just are another way to distribute software.
I do not like them for current apps. They include all the dependencies, more like Windows does with all applications.

But if you have new install and want to run a very old version of some software, then a snap may work, if it exists. Or the other way around, if you have an older install, but want the newest bit of software, then you could run a snap. But you are dependent on updates to snaps.

What drive are you not seeing, the NTFS one? If so then that is probably a Windows issue.
Most often you have left fast start up on which sets hibernation flag or have hibernated Windows. Or maybe Windows needs chkdsk or other repairs.

When you unplug a device, that name is still used, so when you plug it back in, it cannot use that name over again.
Best not to often unplug external drives anyway, if depending on them for data.

---

### Post by linux.girl on 2019-05-29
Thanks oldfred!

The drive that I am not seeing is an internal drive, I don't remember what was in it, I was hoping a could see it on ubuntu, format it and use it for storage. My main drive is TB so the extra space of the second drive would be nice, but I don't know how to access it without seeing it. 

Thanks for tips on snaps and loops, will learn more about it!

---

### Post by oldfred on 2019-05-29
You show three drives, sda, sdb, & sdc.
It looks like install is on sdb, and sdc is external.
Your sda is NTFS, but if you used it with Windows it may have left hibernation (fast start up) flag on. Then the Linux NTFS driver will not mount it read/write. You have to use Windows to clear hibernation flag. You can force mount read only manually. 

Best not to use NTFS unless you have Windows as it periodically will need defrag, chkdsk or other repairs that you cannot do from Linux. If you have a Windows repair disk you can do that maintenance also.

---

### Post by linux.girl on 2019-05-30
What I have now is as follows as per lsblk:

sda                 8:0    0   3.7T  0 disk
&#9492;&#9472;sda1              8:1    0   3.7T  0 part /media/x/MyPassport5 - external media for storage of 4GB
sdb                 8:16   0   3.7T  0 disk
&#9492;&#9472;sdb1              8:17   0   3.7T  0 part /media/x/MyBook4 - external media for storage of 4GB
sdc                 8:32   0 931.5G  0 disk
&#9492;&#9472;sdc1              8:33   0 931.5G  0 part - internal media main disk 1TB
  &#9500;&#9472;ubuntu--vg-root
  &#9474;               253:0    0 930.4G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1
                  253:1    0   976M  0 lvm  [SWAP]
sr0                11:0    1  1024M  0 rom


Missing: the second internal disk that I have inside the PC.

Thanks!

---

### Post by oldfred on 2019-05-30
Does your UEFI/BIOS show another drive. It has list of drives and if not discovered by UEFI/BIOS and reported to operating system it will never be seen. This is in UEFI/BIOS hardware tab, not boot tab. Boot tab will only show bootable devices.

---

### Post by linux.girl on 2019-05-30
Nope, doesn't appear there, might it be one of those stupid cases where my internal second drive got cable disconnected for some reason? I will open the PC and check it out.

---

