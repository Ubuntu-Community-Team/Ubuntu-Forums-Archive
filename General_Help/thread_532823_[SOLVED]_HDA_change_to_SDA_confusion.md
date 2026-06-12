---
title: "[SOLVED] HDA change to SDA confusion"
date: 2007-08-23
forum: General Help
---

### Post by Bukunut on 2007-08-23
Hi,

Well I think I got myself completely confused on this matter and would like help on kindly sorting this.
When I bootup it COULD either boot with my drives being shown as 'HDA' OR 'SDA'  it's a bit of a guessing game, and I am at a loss WHY this happens, it probably is something simple to fix, but.. as yet I have overlooked it.
I have read through quite a few threads that touch on this but not sure what the solution really is here. 

Here is the fstab should it be helpful.. I am sure there is many faults in it that are causing a problem:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=0860fc79-4bfc-4378-b500-33603e2bb043 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb5
UUID=42bbc46e-4bbb-41c3-bff3-908d301d96ed none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /proc auto user,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda3 /media/hda3 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0

 2.6.20-16-generic #2 SMP i686 GNU/Linux

-----UPDATE-------------

I changed the fstab to the following to set the drives as they should be and add the other internal cd/dvd that was missed off the fstab.. the only problem with this is that if bootup wants to change the drives to be HD? again I will get a fail boot again. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=0860fc79-4bfc-4378-b500-33603e2bb043 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb5
UUID=42bbc46e-4bbb-41c3-bff3-908d301d96ed none swap sw 0 0
/dev/sdc0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdc1 /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdc /proc auto user,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda3 /media/hda3 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
Thank you in advance - Bukunut

---

### Post by PentaxFollower on 2007-08-23
What kind of drives do you have in your box? PATA(IDE), SATA or SCSI?

---

### Post by Bukunut on 2007-08-23
Pentaxfollower 

Thank you for your reply. The drives are as follows:-

1. SEAGATE ST3120022A 120GB Hard Drive UDMA100 Model 

2. SEAGATE ST340810A 40.08GB Hard Drive UDMA100 Model 

Sorry, this area I ought to get to know more about, but I now feel like a real noob!! (blush) does this mean they are IDE ATA?

Bukunut

---

### Post by PentaxFollower on 2007-08-23
Yes, all of them are IDE type.
Drive with desriptor SDA is first SCSI (or SATA) disk, and HDA is master disk on Primary IDE controller.
In case of /dev/hdax , x is number of partition. Range 1..4 is reserved for primary partitions, higher numbers are logical partitions.

---

### Post by Bukunut on 2007-08-23
> **PentaxFollower said:**
> Yes, all of them are IDE type.
Drive with desriptor SDA is first SCSI (or SATA) disk, and HDA is master disk on Primary IDE controller.
In case of /dev/hdax , x is number of partition. Range 1..4 is reserved for primary partitions, higher numbers are logical partitions.

Pentaxfollower, thankyou.

I have just had all the drives correctly working with partitions being SDA1 (1 as an example) by editing fstab then 'mount -a'
Now I have rebooted, this time its now changed to HDA1.(!).. I don't understand why the partitions change as they do so often. Is there anyway of updating my **/etc/fstab** to overcome this?

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8267    66404646    7  HPFS/NTFS
/dev/hda2            8268        8395     1028160   82  Linux swap / Solaris
/dev/hda3            8396       14593    49785435    b  W95 FAT32
stephen@bukunut:~$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris

Best wishes - Bukunut

---

### Post by PentaxFollower on 2007-08-23
The sure thing is, your partitions should be /dev/hdax. I don't know why they switch to /dev/sda in your /etc/fstab. 
Maybe try to backup your current fstab and write new one with help of [THIS]("http://ubuntuforums.org/showthread.php?&t=283131") howto. You can also find "sudo fdisk -l" useful, it will list all of your filesystems so you'll know their correct descriptors.

(Before messing with fstab it's good idea to have some liveCD)

---

### Post by Bukunut on 2007-08-23
Pentaxfollower. 

Thank you for that I will have a read and tryout the link you sent. 
Wonder if changing some lines to UUID will benefit?

Thank you - bukunut

---

### Post by PentaxFollower on 2007-08-23
Guess i missed something in your previous post.
Is there someting wrong with your partitions when they are mounted as /dev/hdaX (or hdbX)?
Will they switch to /dev/sda or /dev/sdb after reboot? Are there any partitions missing?
Please, paste the result of "sudo fdisk -l" too.

---

### Post by raijinsetsu on 2007-08-23
They're not setup as a raid are they?
Also, your cd-rom drives will most definitely be hdx not sdx... don't know what's going on there. SATA CD/DVD drives are still pretty new.

If you can boot, type "mount" to list all your mounts. You should see exactly what device is mounted where. Post that here...

---

### Post by Bukunut on 2007-08-23
Pentaxfollower

The oddity began when I noticed that rather than having the icons on the desktop of my windows and backup drive, and the path for Amarok to find my music files the drives had changed HDA>SDA and this happens on each reboot but its a guessing game to which it's gonna be!
If it's one of them boot ups where all is fine and fstab matches partitions.etc there are no problems and all is well. If it's a boot where FSTAB says HDA5 then sysinfo will show SDA5 i change fstab accordingly, depending which direction is gotta be changed to.
It's crazy. 

Bukunut.


stephen@bukunut:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8267    66404646    7  HPFS/NTFS
/dev/hda2            8268        8395     1028160   82  Linux swap / Solaris
/dev/hda3            8396       14593    49785435    b  W95 FAT32

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris
stephen@bukunut:~$

---

### Post by Bukunut on 2007-08-23
raijinsetsu

>   
They're not setup as a raid are they?

Hiya!
How do I know or find this out?
here is the paste as requested!

 I have just changed fstab slighlty as an auto file was created after installing and running **ntfs-config.**

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=0860fc79-4bfc-4378-b500-33603e2bb043 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/hdb5 :
UUID=42bbc46e-4bbb-41c3-bff3-908d301d96ed none swap sw 0 0
/dev/hdc0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc1 /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /proc auto user,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda3 /media/hda3 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hda1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0

stephen@bukunut:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda3 on /media/hda3 type vfat (rw,utf8,umask=007,uid=0,gid=46)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222,uid=0,gid=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)


Just going to reboot to see what happens now. 

regards - Bukunut

---

### Post by raijinsetsu on 2007-08-23
> **Bukunut said:**
> 
/dev/hdc0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc1 /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /proc auto user,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0


These are very very wrong....
You should never mount anything to /proc, as that's a system directory. There is already a fstab line for mounting the proc directory (very first uncommented fstab line).
Also, the floppy driver should be "/dev/fd0" or similar, you're using "/dev".
Last thing, mounting "/dev/hdc0" and "/dev/hdc1"... You have to mount "/dev/hdc" and "/dev/hdd" as your cdroms, assuming that they're on the second IDE channel. You don't mount the partitions of a cd-rom, you mount the whole drive.

type "ls /dev/hd*" and list the output...

---

### Post by Bukunut on 2007-08-23
raijinsetsu

Ok, I am glad you have said there is something wrong with it. That COULD explain the weird actions on each reboot? eg.....now after reboot

stephen@bukunut:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
stephen@bukunut:~$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8267    66404646    7  HPFS/NTFS
/dev/sda2            8268        8395     1028160   82  Linux swap / Solaris
/dev/sda3            8396       14593    49785435    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4664    37463548+  83  Linux
/dev/sdb2            4665        4865     1614532+   5  Extended
/dev/sdb5            4665        4865     1614501   82  Linux swap / Solaris

the results for :-
stephen@bukunut:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5  /dev/sdc  /dev/sdd  /dev/sde  /dev/sdf
[had to change hd* to sd* for this to work]

Obvious output but....
stephen@bukunut:~$  "ls /dev/hd*"
bash: ls /dev/hd*: No such file or directory

OK, so also would I need to change that all will be stable and correct, are these the reasons for the problems perhaps?

Bukunut

---

### Post by raijinsetsu on 2007-08-23
It could be... It really doesn't make sense that sometimes it's HD* and sometimes SD*...
You should definitely change those lines like I said.

The connector on the drives is about 2 inches wide and has about 30 pins, right? Same for your cd-rom drives, right?

---

### Post by Bukunut on 2007-08-23
> The connector on the drives is about 2 inches wide and has about 30 pins, right? Same for your cd-rom drives, right?

Correct. 

I have changed the lines of the fstab as you mentioned, and rebooted, it's back to HD* again, maybe those changes were al that were required, due to time constraints I will not be able to check until later now.I will update the situation on reboot.  :-

The system is saying it cannot read from the cd's now (hdc and hdd), when entering lets say music cd and trying to look at contents in Konq'. :-( 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=0860fc79-4bfc-4378-b500-33603e2bb043 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/hdb5 :
UUID=42bbc46e-4bbb-41c3-bff3-908d301d96ed none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda3 /media/hda3 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hda1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0

---

### Post by raijinsetsu on 2007-08-23
Probably... On your next reboot, make sure everything mounts ok, ie. mount the cdroms and the floppy(with disks in the drives), just to make sure the lines are correct. If they're not, you shouldn't have to reboot to fix them now :)

---

### Post by Bukunut on 2007-08-24
Well. I have rebooted three separate times to see what the outcome would be and pleased to say the problems of the contents appear to be the culprit of the HD* SD* oddity! The cdroms are now not mounting properly and I am trying to see why that is. Once again **thank you for your help,** and if you think you know what possibly could be the reason for the error with cdroms, I would be glad to hear.

This is one area I have never really touched upon and realise that I actually knew so little on this area of linux, I am glad I have read up on this and getting to know and the right syntax. Love the fact that everyday we learn something new.

Regards - bukunut:)

---

### Post by raijinsetsu on 2007-08-24
Hmm... What is the error message when attempting to mount the cdrom?
Also, do another listing of "ls /dev/hd*"
You should have hda,hdb,hdc,and hdd... But I'd like to check.

---

### Post by Bukunut on 2007-08-25
raijinsetsu

Hereis the output as requested. it appeasrs to be normal...

stephen@bukunut:~$ ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda3  /dev/hdb  /dev/hdb1  /dev/hdb2  /dev/hdb5  /dev/hdc  /dev/hdd

Weirdly, when I put a cd into the drive an icon appears on the desktop and then the menu comes up for further actions (in this case open window to explore contents is selected)  The address bar of Konq' says **audiocd:/** 
So now we try the second drive and enter a cdrom,  this time after selecting to explore the contents, the SAME files are shown and once again Konq' shows **audiocd:/** (the same thing)

If I were to put a cdrom into the second drive only, the drive reports back with 'could not read' and **audiocd:/?device=/dev/hdd ** showing in the address bar.

Clicking both the icons on the desktop brings the same result of the same contents showing only of drive number 1 .. ie hdc. Weird. 

Thought I would check what the details were for the drives ...
  
*-cdrom:0
       description: DVD reader
       product: JLMS XJ-HD166S
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: DS1A
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: LITE-ON LTR-52327S
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: QS55
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdd


This is correct isn't it?
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

What I am trying to get my head around is using sysinfo:/ in Konq' the drives show correctly and can be explored correctly as **media:/hdd** and vice versa.

regards Bukunut

---

### Post by Bukunut on 2007-08-25
Just did a reboot and now we are back to the SD* flavour again! So the corrections have NOT stopped the changing.  

/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5  /dev/sdc  /dev/sdd  /dev/sde  /dev/sdf

Am I missing something?? 

Bukunut

---

### Post by raijinsetsu on 2007-08-27
That just doesn't make any sense. There should be no normal way of doing that.
Seeing as your computer is still booting, I would say that this is a problem with udev, but I can't say for sure. Even if it is udev, it doesn't make sense that the HD* drives aren't listed anymore.
It could also be a problem with your IDE controller(either it being partially supported). Let me do some digging...

Oh, do a "lspci" and post the results. Try to get a listing for when the drives are SD and when their HD.

---

### Post by Bukunut on 2007-08-28
raijinsetsu

I started to think about re-installing yesterday, I have done a couple of upgrades of kubuntu on this comp'  and considered a fresh one to overcome the issues here..BUT...thought why,?? There would be nothing to learn from that. So it will be interesting to see what the matter is here.  
I am going to post the results of the SD* boot when I have cleared the work I am doing, but as it has decided (cough) the HD* boot would be a nice change... here it is:-

stephen@bukunut:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

regards - Bukunut

---

### Post by raijinsetsu on 2007-08-28
Ok... I think the problem is your Raid Controller... Go into your BIOS, and make sure raid is disabled. Depending on your BIOS, this setting can usually be found under "Peripherals" or "Disks".

---

### Post by Wolki on 2007-08-28
Inside the kernel, the method for accessing ide harddisks is changing, as the sata driver can now handle pata drives as well, and on some systems does already. It's very strange that your system is deciding which one to choose randomly, but I guess everything can happen...

Ubuntu devs recommend adressing the drives by UUID. Find the UUID for a certain drive by using "sudo vol_id /dev/<drive>" and noting the line starting with "ID_FS_UUID=", then edit the fstab and replace the /dev/something with "UUID=<number found with the command above>".

[edit] You can also use the command "blkid" to show the UUIDS for all your partitions.

---

### Post by Bukunut on 2007-08-31
Wolki, raijinsetsu

Thank you both very much for your kind help.
Glad it gave me a chance to learn about something that i have never bothered with before.
I have changed fstab to the UUID format and all seems well, not rebooted so not sure what will happen with the SD* HD* lotto. Also I checked raid in bios. The error originally in fstab was the problem I guess. 

Thank you - bukunut

---

