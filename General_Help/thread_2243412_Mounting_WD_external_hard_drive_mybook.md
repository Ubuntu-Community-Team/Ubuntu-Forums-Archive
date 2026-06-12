---
title: "Mounting WD external hard drive mybook"
date: 2014-09-08
forum: General Help
---

### Post by daniel179 on 2014-09-08
Tried to find a solution to my question by looking first to the questions already asked about it, but couldn't find anything suitable, some I'm trying my luck:
Got an external hard drive (mybook western digital) by someone who didn't know I'm using Linux. Of course, when I just plug in through the USB slot, the hard drive seems to work (so no visible/hearable defect here), but my Ubuntu (13.10) doesn't recognize it (doesn't appear as a pop-up, nor in the file commander/explorer).
I got already so far in my knowledge that most probably the reason is that I have to mount the hard drive first.
I did already the following commands (from other forums and suggestions) and got the following results:
```
~# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:d601 Foxconn / Hon Hai 
Bus 001 Device 004: ID 8087:07da Intel Corp. 
Bus 001 Device 003: ID 08ff:168f AuthenTec, Inc. AES1660 Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1058:1230 Western Digital Technologies, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@daniel-SVS1512Z9EB:~# apt-cache policy cifs-utils
cifs-utils:
  Installed: (none)
  Candidate: 2:6.0-1ubuntu2
  Version table:
     2:6.0-1ubuntu2 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
as well as ~# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1
root@daniel-SVS1512Z9EB:~# fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a4fe5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   83  Linux
```
So now I've got two questions:

[LIST=1]
[*]Providing that it really is only the mounting I have to do, how do I do it best?
[*]Do I then have to "unmount" it every single time as well? If so, how to do that?
[/LIST]
Thanks a lot in advance and best regards,
Daniel

---

### Post by lisati on 2014-09-08
Not a networking or wireless issue.
*Thread moved to **General Help**.*

---

### Post by daniel179 on 2014-09-08
Apologies and thx for moving it.

UPDATE:

just installed gparted to try to get more info. 

I think that in pic 1 the sda5 partition is the wd hdd, as once I click on it twice it says in pic 2 that it is not yet mounted, as well as the warning. 

Any suggestions?

Thanks in advance and best regards,
Daniel

---

### Post by coffeecat on 2014-09-08
sda5 looks as though it could be your encrypted Ubuntu installation, not the WD hard drive. From the information you gave in your first post, your WD hdd would probably be sdb and the single partition on it, sdb1. Pity then that you did not include the fdisk output for sdb. 

Plug the WD hdd in, switch it on, and then post the complete output of these terminal commands:

```
mount
sudo parted -l
sudo fdisk -l
```

A question and a comment: have you installed any applications such as usbmount? If you have installed usbmount, uninstall it.

You are running Ubuntu 13.10, which is past end-of-life and now unsupported. Our help for this can be limited only to investigating whether there is a fault with the WD HD. You need to be preparing for upgrading to 14.04 or re-installing with 14.04.

---

### Post by daniel179 on 2014-09-08
Hi CoffeeCat....thanks first of all for the hint on ubuntu14.......actually this is partially why I wanted to solve the question of the external hard drive, because I want to first free some space from my internal hard drive onto the external one in order to then install the new ubuntu version.....

here the output on the commands you proposed:

**MOUNT**

```
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=daniel)
```

[B]sudo parted -l

[/B]```
Model: ATA WDC WD10JPVT-55A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical
```


[B]sudo fdisk -l

[/B]```
Model: WD My Book 1230 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4001GB  4001GB  primary




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0,00B  991GB  991GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8464MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0,00B  8464MB  8464MB  linux-swap(v1)




Error: /dev/mapper/sda5_crypt: unrecognised disk label
```






Thanks in advance!

---

### Post by daniel179 on 2014-09-08
Oh yeah, and you were right.....it's the sdb1......

here in attachment the screenshot of gparted with the error (not supporting ntfs)

---

### Post by coffeecat on 2014-09-09
I've added BBCode tags to make your terminal output readable by restoring formatting. Unfortunately, you chose to edit the outputs of both parted and fdisk, which makes both of them less than useful. When someone asks you to post the **complete** output of something, please post the complete output. Terminal output needs to be enclosed in code tags - see here: [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

As to your sdb1 partition in your WD hard drive, I was 99% sure that it was going to be a ntfs partition from your description in your first post, and the failure to mount that you described suggested something seriously wrong with the drive or with your Ubuntu installation. Normally with a NTFS-formatted drive, you simply plug it in and switch it on and it gets automounted. The error from gparted tells us why this is not happening - a missing ntfs-3g driver - but what worries me is why you are missing the ntfs-3g driver. There is absolutely no reason to uninstall it - did you know that it has been uninstalled?. Normally, I would suggest that you simply reinstall ntfs-3g, but you are running an unsupported version of Ubuntu and the repositories are closed. There is a way round that, but with one inexplicable problem in your installation, there could be others, so I suggest you make a fresh installation of 14.04. Don't try to upgrade using the old-releases repositories because that will bring over to your upgraded installation whatever else is wrong. If you make a fresh installation of 14.04, you should have no problems with that WD drive.

---

### Post by daniel179 on 2014-09-09
thanks for the help coffeecat....

the problem I have is that if i would make a completely fresh installation of ubuntu 14.04. I would lose a lot of data I would have to save first.....for that I would need a hard drive or any other solution for that matter....

---

### Post by Habitual on 2014-09-09
I use the udisks command as shown at [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Per-User_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Per-User_Mounts)

Does it **have** to be NTFS?
I have a WD MyBook 3G and I nuked it with gparted and created an ext4 filesystem.
Linux doesn't know or care about NTFS filesystem attributes or permssions. It's "messy" to get the perms just right so you can read-write your own stuff.

I mount it like so:
```
**[COLOR=#FF0000]/usr/bin/udisks --mount /dev/sdb1 /media/<user>/internal[/COLOR]**
```
and it "just works".

I wrote it up over [here...]("http://bournetoraiseshell.com/article.php?story=2014082617294656")
and not a single fstab entry was needed. I mount and umount at will when I need it. And it survives reboots.

Hope that helps.

---

### Post by Derrick_Robert on 2015-03-09
Hey Guys,

[FONT=arial]Can anybody suggest a NAS device that is good with this piece of software? Currently I back up a client PC Win 7 64 bit, to an external hard drive, I'd like to backups from the machine to a NAS device. Anybody have any recommendations?

Thanks a lot![/FONT]

---

### Post by coffeecat on 2015-03-10
This thread concerns an obsolete version of Ubuntu, and the OP has not come since September last. Thread closed.

@Derrick_Robert, it sounds as though you are using Windows. This is an Ubuntu forum. If you have a problem with Ubuntu, or need recommendations for NAS devices that work with Ubuntu, please start your own thread.

---

