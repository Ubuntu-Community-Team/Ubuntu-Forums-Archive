---
title: "Please help NAS + USB thumb drives + Raid 6"
date: 2021-08-29
forum: General Help
---

### Post by cancerguy2016 on 2021-08-29
Part 2
Hello Everyone,

I want to thank everyone for your help. I did get the raid 5 to work with 5 usb thumb drives. However I can't seem to mount them into a simply folder or drive letter. below is all my info I can think of to give you.

1. I want to be able to simply see the 5 drives as one drive.
2. I want to be able to map the drives to various family members some in the house and others in another city.
3. I don't care about speed or anything just that is holds the data. This is my oh crap the house is on fire little mini computer that I can grab and all my data is saved machine. 


_______________________________________________________________________________________________________________________

monty@NAS:~ $ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME          SIZE FSTYPE            TYPE  MOUNTPOINT
sda           1.9T                   disk
&#9492;&#9472;sda1        1.9T linux_raid_member part
  &#9492;&#9472;md127     7.6T                   raid5
sdb           1.9T                   disk
&#9492;&#9472;sdb1        1.9T linux_raid_member part
  &#9492;&#9472;md127     7.6T                   raid5
sdc           1.9T                   disk
&#9492;&#9472;sdc1        1.9T linux_raid_member part
  &#9492;&#9472;md127     7.6T                   raid5
sdd           1.9T                   disk
&#9492;&#9472;sdd1        1.9T linux_raid_member part
  &#9492;&#9472;md127     7.6T                   raid5
sde           1.9T                   disk
&#9492;&#9472;sde1        1.9T linux_raid_member part
  &#9492;&#9472;md127     7.6T                   raid5
mmcblk0     119.4G                   disk
&#9500;&#9472;mmcblk0p1   256M vfat              part  /boot
&#9492;&#9472;mmcblk0p2 119.1G ext4              part  /

_______________________________________________________________________________________________________________________

monty@NAS:~ $ sudo mdadm --detail /dev/md/vol1
/dev/md/vol1:
           Version : 1.2
     Creation Time : Sat Sep 11 15:59:22 2021
        Raid Level : raid5
        Array Size : 8191465472 (7811.99 GiB 8388.06 GB)
     Used Dev Size : 2047866368 (1953.00 GiB 2097.02 GB)
      Raid Devices : 5
     Total Devices : 5
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Sat Sep 11 17:29:38 2021
             State : clean, degraded
    Active Devices : 4
   Working Devices : 5
    Failed Devices : 0
     Spare Devices : 1


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : NAS:vol1  (local to host NAS)
              UUID : 8573b247:39eaf031:adf781e0:e99a7467
            Events : 328


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       65        1      active sync   /dev/sde1
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
       -       0        0        4      removed


       5       8       49        -      spare   /dev/sdd1

_______________________________________________________________________________________________________________________

monty@NAS:~ $ sudo mkfs.ext4 /dev/md127
mke2fs 1.44.5 (15-Dec-2018)
Creating filesystem with 2047866368 4k blocks and 255983616 inodes
Filesystem UUID: e74a0996-39f7-46e9-8a72-3bee6edb3923
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544, 1934917632


Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
**_Writing superblocks and filesystem accounting information: mkfs.ext4: Input/output error while writing out and closing file system_ <==== Failed**




_______________________________________________________________________________________________________________________

monty@NAS:~ $ sudo fdisk -l /dev/sda
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sda: 1.9 TiB, 2097152000000 bytes, 4096000000 sectors
Disk model: Flash Disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 92F614EE-33EC-6945-ABC8-3FB798FE06EC
Device     Start        End    Sectors  Size Type
/dev/sda1   2048 4095999966 4095997919  1.9T Linux filesystem

monty@NAS:~ $ sudo fdisk -l /dev/sdb
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdb: 1.9 TiB, 2097152000000 bytes, 4096000000 sectors
Disk model: ProductCode
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 46216C9D-2202-8E40-8908-527B613911D0
Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 4095999966 4095997919  1.9T Linux filesystem

monty@NAS:~ $ sudo fdisk -l /dev/sdc
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 1.9 TiB, 2097152000000 bytes, 4096000000 sectors
Disk model: ProductCode
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A6796A45-2BB9-2B4A-8050-B63AB0A44207
Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 4095999966 4095997919  1.9T Linux filesystem

monty@NAS:~ $ sudo fdisk -l /dev/sdd
Disk /dev/sdd: 1.9 TiB, 2097152000000 bytes, 4096000000 sectors
Disk model: ProductCode
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 98B6478B-AF3A-AF48-8064-82C3357E58EE
Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 4095999966 4095997919  1.9T Linux filesystem

monty@NAS:~ $ sudo fdisk -l /dev/sde
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sde: 1.9 TiB, 2097152000000 bytes, 4096000000 sectors
Disk model: ProductCode
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BEF3AFF5-E4BC-F348-9944-01F000EF0913
Device     Start        End    Sectors  Size Type
/dev/sde1   2048 4095999966 4095997919  1.9T Linux filesystem

_______________________________________________________________________________________________________________________

monty@NAS:~ $ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md127 : active raid5 sde1[1] sdd1[5](S) sdc1[3] sda1[0] sdb1[2]
      8191465472 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [UUUU_]
      bitmap: 16/16 pages [64KB], 65536KB chunk


unused devices: <none>

_______________________________________________________________________________________________________________________

monty@NAS:~ $ blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="B05C-D0C4" TYPE="vfat" PARTUUID="ea3da200-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="075b0d0c-7b1e-4855-9547-125591698723" TYPE="ext4" PARTUUID="ea3da200-02"
/dev/sda1: UUID="8573b247-39ea-f031-adf7-81e0e99a7467" UUID_SUB="a437ffd6-2d1c-14a7-72bb-167f5ae5053c" LABEL="NAS:vol1" TYPE="linux_raid_member" PARTUUID="f6603124-01bc-484b-8a04-6c072782f320"
/dev/sdb1: UUID="8573b247-39ea-f031-adf7-81e0e99a7467" UUID_SUB="31aa01dd-8184-cfdc-4e17-9a5d51b2baef" LABEL="NAS:vol1" TYPE="linux_raid_member" PARTUUID="8d7064c5-f8bb-1c44-9e67-1278845c855b"
/dev/sdc1: UUID="8573b247-39ea-f031-adf7-81e0e99a7467" UUID_SUB="e66c2700-b587-141a-500e-260d83ca30f9" LABEL="NAS:vol1" TYPE="linux_raid_member" PARTUUID="f13efa61-7c1f-7941-8f8a-c62268e29616"
/dev/sdd1: UUID="8573b247-39ea-f031-adf7-81e0e99a7467" UUID_SUB="9ef608c4-466d-60cb-b624-9862f041757a" LABEL="NAS:vol1" TYPE="linux_raid_member" PARTUUID="4c4a6d8b-e000-e04b-8bb8-854554056e4c"
/dev/sde1: UUID="8573b247-39ea-f031-adf7-81e0e99a7467" UUID_SUB="bffb2a7f-b102-8400-f428-a1cab5d071c9" LABEL="NAS:vol1" TYPE="linux_raid_member" PARTUUID="becfb34b-540e-9545-91ac-3d559796bdaf"



________________________________________________________________________________________________________________________________________

Part 1
Hello Everyone,

My name is Jonathan and I am new to using Ubuntu. I started off wanting to 3d print then got into Octopi and now I want to make a NAS. I have a RPI 4 8GB with a USB Hat. I have 6 available slots and each slot has a 2TB Thumb Drive. I am following this guide: [https://www.ricmedia.com/build-raspberry-pi3-raid-nas-server/](https://www.ricmedia.com/build-raspberry-pi3-raid-nas-server/) and I am getting hung up on Section Setup Drives and Raid Volume. I type everything exactly. I have even formatted the USB drives multiple times and formatted my MicroSD card many times as well thinking the install messed up. I did notice my sudo blkid has extra in it the Label_Fatboot="boot". I don't know why this is. Please can someone help me. I want to put my 6 2TB USB drives into Raid 6 so I can network map this to one drive instead of 6 drives. If no one know how to do this I guess I will just map 6 different drives. Oh and I installed Samba and MDADM. I thank you in advance for any help you can give me.   

pi@NAS:~ $ sudo blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="B05C-D0C4" TYPE="vfat" PARTUUID="c70dc193-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="075b0d0c-7b1e-4855-9547-125591698723" TYPE="ext4" PARTUUID="c70dc193-02"
/dev/sda1: LABEL="USB02" UUID="AE9A-60DC" TYPE="exfat" PARTUUID="fa2cb833-01"
/dev/sdb1: LABEL="USB04" UUID="50D4-C2AC" TYPE="exfat" PARTUUID="fa2cb833-01"
/dev/sdc1: LABEL="USB01" UUID="3682-823D" TYPE="exfat" PARTUUID="a2b75359-01"
/dev/sdd1: LABEL="USB05" UUID="08EF-AA4D" TYPE="exfat" PARTUUID="fa2cb833-01"
/dev/sde1: LABEL="USB06" UUID="820A-61DE" TYPE="exfat" PARTUUID="fa2cb833-01"
/dev/sdf1: LABEL="USB03" UUID="ACBC-C8FC" TYPE="exfat" PARTUUID="fa2cb833-01"
/dev/mmcblk0: PTUUID="c70dc193" PTTYPE="dos"
pi@NAS:~ $ sudo mdadm --create --verbose /dev/md/vol1 --level=6 --raid-devices=6 /dev/sd[a1-f1]
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sda: Device or resource busy
mdadm: ddf: Cannot use /dev/sda: Device or resource busy
mdadm: Cannot use /dev/sda: It is busy
mdadm: cannot open /dev/sda: Device or resource busy

---

### Post by TheFu on 2021-08-29
a) this is a terrible idea.  flash storage shouldn't be used in a RAID, ever.  But you'll probably need to learn that yourself. Flash storage have write limitations and RAID will be abusive towards that hardware. May last 1 yr before needing replacement.  USB-storage isn't the same protocol as SATA or eSATA either. You'll see.

b) don't format with exfat. You need to partition the flash drives with a GPT table, create at least 1 partition on each of the devices that is **exactly** the same size, and point **mdadm** at those partitions.

c) After mdadm creates the "array", use **mkfs** to create a file system (probably should use **f2fs**, but ext4 would be the normal choice on SSD or HDD drives) on that new device. The device name should be /dev/md0 or some other number at the end.  f2fs is a native Linux file system, with POSIX support that is designed to be used by flash storage. I think it is in the f2fs-utils package. Install that.

d) After the array has a file system, modify the fstab to mount the storage.

BTW, you can use other storage volume management solutions rather than mdadm.  LVM or ZFS.  ZFS has RAIDz2, which is similar to RAID6. Of these 3, zfs is the newest, proven solution. It is a completely different way of thinking about file systems.

Just because something is possible, that doesn't make it a good idea.  When something bad happens, be prepared.  Read up now about fixing RAID issues. Sometimes the only possible solution is to wipe everything and start over. **RAID never replaces backups.**

---

### Post by TheFu on 2021-08-29
Try
```
sudo mdadm --create --verbose [COLOR="#FF0000"]/dev/md0[/COLOR] --level=6 --raid-devices=6 /dev/[COLOR="#FF0000"]sd[a-f]1[/COLOR]
```

You can also spell out the devices as 
/dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

That's what the last parameter intended, but a1-f1 doesn't get recognized.  Either used letters OR numbers in a sequence and bash should handle it.

---

### Post by cancerguy2016 on 2021-08-29
Hello,

Thank you for trying to help. However it didn't work. Even thought I have watched videos of it working and working amazingly. All drives are the same at 1.9TB. I did both the long written way and short way and got the same message. If you know of anything that could help that would be great. If anyone could help that would be greatly appreciated. 

pi@NAS:~ $ sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sda1: Device or resource busy
mdadm: ddf: Cannot use /dev/sda1: Device or resource busy
mdadm: Cannot use /dev/sda1: It is busy
mdadm: cannot open /dev/sda1: Device or resource busy


 
pi@NAS:~ $ lsblk -o name,size,mountpoint
NAME          SIZE MOUNTPOINT
sda           1.9T
`-sda1        1.9T /media/pi/USB02
sdb           1.9T
`-sdb1        1.9T /media/pi/USB04
sdc           1.9T
`-sdc1        1.9T /media/pi/USB01
sdd           1.9T
`-sdd1        1.9T /media/pi/USB05
sde           1.9T
`-sde1        1.9T /media/pi/USB06
sdf           1.9T
`-sdf1        1.9T /media/pi/USB03
mmcblk0     119.4G
|-mmcblk0p1   256M /boot
`-mmcblk0p2 119.1G /


 Thank you
Jonathan

---

### Post by TheFu on 2021-08-29
you cannot have any device being used in a mdadm array mounted during the array creation.  Need to umount all the current mounts (/media/pi/USB00-xxxx) first.  Did you remove all partitions, lay down a fresh GPT, and add 1 partition marked for Linux RAID use BEFORE the mdadm --create command?

Also, whenever posting commands and output, please, please, please, use code tags. This makes columns line up.

---

### Post by Tadaen_Sylvermane on 2021-08-29
If I may, do not use Raid. As mentioned above other than testing something out doing it with usb is just a bad plan asking for problems. Look for a software called mergerfs. That will pool the drives into a single mountpoint (effectively making it a single volume). If you want some type of raid (depending on your load) snapraid may be more suited. While it isn't ideal for regular full time use due to it being a "snapshot" raid you won't lose anything if one of the usb drives goes wonky other than what's on that drive. You risk the whole array with actual raid and usb.

**&#8203;**[https://perfectmediaserver.com/tech-stack/snapraid.html](https://perfectmediaserver.com/tech-stack/snapraid.html)

---

### Post by TheFu on 2021-08-29
> **Tadaen_Sylvermane said:**
> If I may, do not use Raid. As mentioned above other than testing something out doing it with usb is just a bad plan asking for problems. Look for a software called mergerfs. If you want some type of raid (depending on your load) snapraid may be more suited. While it isn't ideal for regular full time use due to it being a "snapshot" raid you won't lose anything if one of the usb drives goes wonky other than what's on that drive. You risk the whole array with actual raid.

**&#8203;**[https://perfectmediaserver.com/tech-stack/snapraid.html](https://perfectmediaserver.com/tech-stack/snapraid.html)

Media server software understands the idea that there are multiple disks connected and will happily provide a merged view.  I have 3-4 separate disks connected to each of my libraries (Movies, TV, Music, Photos, etc) in plex, jellyfin, and minidlna.  In all the clients, those different storage areas are merged, to where I don't really know exactly which disk where something is stored.  I just add each directory to the library list for "Movies" - like this:
/d/D1/M
/d/D2/M3
/d/D3/M4

RAID solves 2 issues and caused 10+ others.
[LIST]
[*]High Availability - i.e. if a drive fails, it keeps working. This can be important for very few systems inside a business, but 90% don't actually need the HA, so they don't need RAID.  Lots of business systems are nice-to-have and only mandatory a few days a month.
[*]Improved performance, but USB and flash memory is a complete failure if performance it the goal.  A $50 SSD would do 5x, if not 20x better performance. Even better if connected via SATA3 or SAS.  USB bus speeds are never real-world, but neither are SATA or SAS either. ;(
[/LIST]

Playing around with the different RAID to learn and using USB **is** extremely valid.

---

### Post by Tadaen_Sylvermane on 2021-08-30
I apologize. I think you  misunderstood that link. I didn't post it about media center specifically, rather that is where I first found out about mergerfs and snapraid.

Mergerfs is more of a descendant or otherwise of AUFS, a union file system. It presents as many drives as you want as a single mountpoint. This works outside of any media center on the cli, or in my case with Kodi I only have to mount that single NFS share rather than X number of drives separately. The combination with snapraid gives you a safety net in that you can restore a drive if it dies. If you have no backups of said drive then you only lose what's on that drive, not the whole array. It's worked out well for me in media. I've read some people even run KVM virtual machines with it although I'm not sure I'd do that myself. Point being is it's not a bad system really in this case although nothing with USB like this is a good idea. Far safer than a traditional raid or lvm though imho.

You can write to that single mount as well and mergerfs goes by rules you set, in my case it puts whatever on the drive with the most free space. There are options to this, again in my case most free space unless the drive has less than 30gb of free space. Quite configurable.

For a file server that doesn't require high i/o that a raid would likely provide it's a great system I think.

---

### Post by cancerguy2016 on 2021-09-11
Hello Everyone,

First let me say I have been battling Bone Cancer for 5 years. I have had over 30+ surgeries and almost died 7 times. I have gone through very harsh chemotherapy. My brain doesn't work at all like it use to. I am very much dumber than I use to be and it pisses me off because once I could have done this no problem and now I can't do basic things. So please bare with me. I get that most think it is stupid to put usb thumb drives into raid. I am not looking for performance. I am looking for ease of use and ease of connection. I want to be able to have my mom and aunt simply see it as a hard drive on their computer and just drag and drop their information into it. I want to be able to have my kids do it as well. So some people will be on my network and others will be in another city. If **_[COLOR=#000000]mergerfsb[/COLOR]_**[COLOR=#000000] is the best to use then can you provide a step by step guide directions? do I need to format my drives? should I just reload Raspbian and start all over? My usb drives are in a raid 5 so should I delete them and start over with just them as normal drives? 

thank you for the help
Jonathan[/COLOR]

---

### Post by Tadaen_Sylvermane on 2021-09-12
I'm sorry to hear that. My dad is dealing with Multiple Myeloma right now. Stage 4 I think. Doing well at the moment but who knows how long that will last.

Install it then add the drives to your fstab. Then add the mergerfs mount after the usb drives. Here is my fstab for example.

```
# snapraid data drives# b1 bottom left
UUID=e2291a37-4b7d-481c-9f3a-4ef8bc070b50 /snapraid/data/d1 ext4 defaults 0 0
# b1 top right
UUID=3dd21425-8d8d-42eb-8504-1239c75d31fc /snapraid/data/d2 ext4 defaults 0 0
# b1 bottom right
UUID=aea5dbef-ce44-436b-92f6-d3c53d96d187 /snapraid/data/d3 ext4 defaults 0 0
# b3
UUID=0013ad3f-2226-4dca-87df-4348a9db90ed /snapraid/data/d4 ext4 defaults 0 0


# snapraid pooled directory
/snapraid/data/* /snapraid/pool fuse.mergerfs defaults,allow_other,use_ino,noforget,fsname=pool,category.create=mfs,minfreespace=40G 0 0
```

It supports globbing so a single line with a * works just fine. Aside from that it's just any other folder on your system. You can do an NFS or Samba share from it like anything else. As far as the remote access you will need a vpn or sftp. That is out of my knowledge as I have no real need for remote access at the moment.

For snapraid usage you will need to dedicate a drive to parity (it can have up to 6 parity drives I think at the moment). Number of parity drives is number of drives that can fail and still recover from out of the array. Add it to the fstab. Here is my /etc/snapraid.conf

```
parity /snapraid/parity/p1/snapraid.parity

content /var/snapraid/snapraid.content
content /snapraid/data/d1/.snapraid.content
content /snapraid/data/d2/.snapraid.content
content /snapraid/data/d3/.snapraid.content
content /snapraid/data/d4/.snapraid.content


data d1 /snapraid/data/d1/
data d2 /snapraid/data/d2/
data d3 /snapraid/data/d3/
data d4 /snapraid/data/d4/


exclude *.unrecoverable
exclude /tmp/
exclude /lost+found/
exclude /.docker/
exclude /snapraid/pool/video/jworg/meetings/
autosave 500
```

Of course you need to adjust both fstab and snapraid.conf paths to reflect your chosen layout.

And just for good measure my snapraid script I've been working on. I run it twice a week.

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/snapraidsync.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/snapraidsync.sh)

---

