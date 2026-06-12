---
title: "drives no longer automount"
date: 2007-10-19
forum: General Help
---

### Post by Mateo on 2007-10-19
neither USB or SD cards will automount now that i upgraded to gutsy.  how do I fix this.  I need to be able to access these drives urgently.

---

### Post by bodhi.zazen on 2007-10-20
I do not know your problem without more information, but I did have this problem at one point in gutsy testing.

My problem was gnome-volume-manager was not installed, so :

1. Try logging out and back in.

2. Reboot.

3. ```
sudo apt-get install gnome-volume-manager
```

4. check you logs ... [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by jamis on 2007-10-20
Hello I'm having the same problem since upgrading to Gutsy.  None of my external devices (iPod, hard drive, pendrive, etc) will mount.  Here's an example of the error messages: mount: wrong fs type, bad option, bad superblock on /dev/sdc2,  missing codepage or helper program, or other error

I have gnome-volume-manager installed.

dmesg | tail
[ 5832.556000] sdc: Mode Sense: 68 00 00 08
[ 5832.556000] sdc: assuming drive cache: write through
[ 5832.560000] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[ 5832.560000] sdc: Write Protect is off
[ 5832.560000] sdc: Mode Sense: 68 00 00 08
[ 5832.560000] sdc: assuming drive cache: write through
[ 5832.560000]  sdc: sdc1 sdc2
[ 5832.564000] sd 3:0:0:0: Attached scsi removable disk sdc
[ 5832.564000] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 5833.060000] FAT: Unrecognized mount option "usefree" or missing value

 mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=37047bd0-4a98-4bff-97cf-c17ce223d88f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=a7cd0be9-cad1-48b1-8fb8-1d79a330900c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

fdisk
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1787        6811    40363312+  83  Linux
/dev/sda2            6812        7113     2425815    f  W95 Ext'd (LBA)
/dev/sda3   *           1        1705    13695381   83  Linux
/dev/sda4            1706        1786      650632+  82  Linux swap / Solaris
/dev/sda5            6812        7032     1775119+  82  Linux swap / Solaris
/dev/sda6            7033        7113      650601   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1       38913   312568641    b  W95 FAT32
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 4060 MB, 4060086272 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           3       96264    0  Empty
/dev/sdc2               4         123     3855600    b  W95 FAT32


Hopefully we can get this sorted.  Doing some searching shows many other users are experiencing the same problem.  But otherwise everything works great with Gutsy.

---

### Post by jdefaver on 2007-10-20
same here, event with cd/dvd :(

---

### Post by Mateo on 2007-10-20
> **bodhi.zazen said:**
> I do not know your problem without more information, but I did have this problem at one point in gutsy testing.

My problem was gnome-volume-manager was not installed, so :

1. Try logging out and back in.

2. Reboot.

3. ```
sudo apt-get install gnome-volume-manager
```

4. check you logs ... [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Ok, tried reinstalling gnome-volume-manager (weird that that's involved), but it didn't have any change.

i don't know what to look for in the log files.  here's one thing from syslog that might have something to do with it (or might have absolutely nothing to do with it.

```
Oct 19 23:38:05 matthew-desktop kernel: [ 1176.468721] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Oct 19 23:38:05 matthew-desktop kernel: [ 1176.469350] device-mapper: ioctl: error adding target to table
```

that line is repeated probably a hundred times in the syslog file.

---

### Post by Mateo on 2007-10-20
bump

---

### Post by Goliash on 2007-10-21
I have upgraded to Kubuntu 7.10 and I have the same problem. No drives can't automount - DVD medias, SD card or USB key. I ask the same, how can I fix it?
> [61703.212000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[61703.212000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[61703.212000]  sdb: sdb1 sdb2
[61703.212000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[61703.212000] sd 5:0:0:0: Attached scsi generic sg2 type 0

All medias can be mounted manually.

---

### Post by Mateo on 2007-10-21
i know, lots of people have this problem but it looks like no one has a solution.

---

### Post by bodhi.zazen on 2007-10-21
have you considered filing a bug report ?

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by Mateo on 2007-10-21
i know how to file a bug report.  unfortunately, since i have 0 idea what is causing the bug, it's hard to help them find a solution.  besides, i've filed at least a dozen bug reports and 0 have ever been fixed, in fact many have never even been responded to.  i find it's easier to get help here or on irc.  feel free to file a bug report if you wish, though.

---

### Post by Goliash on 2007-10-21
I feel it the same. I wanted to ask if it is possible somewhere to set automount off or on. It should be a possibility to do this somewhere. I don't really know what daemon takes care of that and I would like to find out here. I hoped somebody will tell me.

---

### Post by bodhi.zazen on 2007-10-21
> **Goliash said:**
> I feel it the same. I wanted to ask if it is possible somewhere to set automount off or on. It should be a possibility to do this somewhere. I don't really know what daemon takes care of that and I would like to find out here. I hoped somebody will tell me.

gnome-volume-manager

---

### Post by Goliash on 2007-10-21
I have already posted that I use Kubuntu. So maybe Hal, Dbus or something like them, maybe there is some frontend in KDE but gnome-volume-manager is useless for me.

---

### Post by Mateo on 2007-10-21
gnome-volume-manager handles automount?  huh?

---

### Post by Mateo on 2007-10-21
so, i type gnome-volume-manager in the terminal and nothing happens.

---

### Post by Mateo on 2007-10-22
anyone here made headway on this one?  i'm still experimenting.

---

### Post by Goliash on 2007-10-22
No, still mounting manually :-(

---

### Post by Goliash on 2007-10-22
I think we should report bug that [automounting]("http://docs.kde.org/userguide/multimedia.html#automounting") doesn't work. Finally I found where it can be set: Kcontrol -> Peripherals -> Storage Media -> Advanced

---

### Post by Mateo on 2007-10-22
i already reported the bug.

[https://bugs.launchpad.net/ubuntu/+bug/155408](https://bugs.launchpad.net/ubuntu/+bug/155408)

i notice that it usually takes a week or more to get a first reply (sometimes you never get one).  it's dfficult for bugs to be fixed unless they know what is causing them i think.

I can't find any options for automount in Gnome.

---

### Post by Mateo on 2007-10-22
here's my dmesg:

```
[ 7752.053587] sd 4:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[ 7752.058416] sd 4:0:0:0: [sdb] Write Protect is off
[ 7752.058420] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 7752.058422] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7752.063414] sd 4:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[ 7752.068484] sd 4:0:0:0: [sdb] Write Protect is off
[ 7752.068488] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 7752.068490] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 7752.068494]  sdb: sdb1

```

---

### Post by Mateo on 2007-10-22
**FIXED** mine.

Goliash, this is what worked for me.  edit the file /etc/fstab.  Somehow lines got added on the upgrade. I removed the lines related to my removeable media /dev/sdb1 was the one I was having problems with.  I saved that and now it works good!

---

### Post by Goliash on 2007-10-23
Can you post here your fstab? I didn't find anything wrong in mine.
> #/dev/sda1
UUID=abb359cb-8b51-4628-a099-36a576c941e1 / ext3 nouser,defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid 0 1

# /dev/sda2
UUID=88131f7e-d439-4f33-85cb-d75dacc2496c /home/goliash ext3 nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2

# /dev/sda3
# UUID=DA24BAAB24BA8A51

# /dev/sda4
UUID=9de31f89-85b9-4e2b-8325-355d8a070eae none swap sw 0 0

/dev/scd0        /media/cdrom0   udf,iso9660 user,utf8,noauto,rw,dev,exec,suid     0       0

/dev/disk/by-id/usb-MSI_MS-551X_0000D104E83C0A8C-0:0-part1 /media/sdb1 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/mmcblk0p1 /media/sd auto user,utf8,umask=000,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1       /media/sdb1     auto    user,utf8,noatime,noauto,rw     0       0

/home/goliash/upload    /home/ftp/upload        none    bind    0       0
/home/goliash/mp3       /home/ftp/mp3   none    bind    0       0
/home/goliash/backup/Programy   /home/ftp/programy      none    bind    0       0
/home/goliash/erase     /home/ftp/erase none    bind    0       0
/media/cdrom    /home/ftp/dvd-rom       none    bind,noauto     0       0


---

### Post by Mateo on 2007-10-24
here's mine:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc               proc         defaults                           0  0  
# /dev/sda3 -- converted during upgrade to edgy
UUID=ecdaa542-3247-4c3e-a636-1f3364a23575  /                   ext2         defaults,errors=remount-ro         0  1  
# /dev/sda1 -- converted during upgrade to edgy
# UUID=3234-38EB                           /media/sda1         vfat         defaults,utf8,umask=007,gid=46   0  1
# /dev/sda2 -- converted during upgrade to edgy
UUID=4627-C44D                             /media/HP_Pavilion  vfat         auto,users,exec,uid=1000,gid=1000  0  0  
# /dev/sda4 -- converted during upgrade to edgy
UUID=7da4b4b6-ee81-47f7-a4a9-60dc3d9d3162  none                swap         sw                                 0  0  
#/dev/hdb                                  /media/cdrom0       udf,iso9660  user,noauto                        0  0  

#/dev/sdb1                                  /media/sdb1         vfat         defaults                           0  0  
```

The last line there was the drive I was having trouble with.  By commenting it out, I no longer have the problem.

---

### Post by zapcojake on 2007-10-24
Try this:

Code:
cd /etc/rc2.d
mv S12hal S13hal


Then reboot.  hald is trying to start before dbus.  This should fix it.

---

### Post by bodhi.zazen on 2007-10-24
that should be ***S13hal*** (with no space)

---

### Post by Goliash on 2007-10-25
Mateo: I tried to comment lines with sdb1 and scd0 but unfortunatelly with no success.

zapcojake: I changed the order but also with no success.

---

### Post by Rumpty on 2007-10-25
I tried plugging in my removable USB drive, and it automounts fine.

There is no entry in fstab for this drive. There is a folder in /media (called kingston in my case) where it automounts.

Running Gutsy, fresh install.

---

### Post by Goliash on 2007-10-25
Yeah, I think that's a problem in my case that I upgraded - I also had some problems with Java (which I have solved) and suspend function is not so good like before upgrade (sometimes it restarts instead of suspend). I have entry in my fstab for sdb1 because of special parameter for vfat - utf8.

---

### Post by Goliash on 2007-10-25
Unfortunatelly I found another problem which I think depends on this. When I burn DVD in K3B and it wants to verify data, it doesn't find DVD.
> [42749.064000] cdrom: This disc doesn't have any tracks I recognize!
[42835.524000] ata1.00: 16 bytes trailing data
[43676.660000] ata1.00: 16 bytes trailing data
[43839.328000] ata1.00: 16 bytes trailing data

I have to pull it out and put it in again. After that I can mount it manually without any problem.

---

### Post by zapcojake on 2007-10-25
> **bodhi.zazen said:**
> that should be ***S13hal*** (with no space)

Yes, thank you

---

### Post by zapcojake on 2007-10-25
Is it feasible for you to just do  a clean install?  I tried going from Kubuntu 7.04 to 7.10 and had some headaches also.

---

### Post by ColombianGold on 2007-10-25
Same problem here...

I was so happy with 7.04 really minor bugs, I thought Gutsy would be the final one...

But automount not working...come on! Ill keep looking for solution.
T60/ x1300 so I have ati problems too...

CG

---

