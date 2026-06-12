---
title: "RAID 1+0 Woes..."
date: 2007-10-25
forum: General Help
---

### Post by DoomCypher on 2007-10-25
Hello everyone, I have absolutely no idea how to set a RAID1+0 array. I already made the necessary configuration in the BIOS; I even installed dmraid, but I've been unsuccessful trying to make a partition inside the device. 

Can someone help me please? Thanks. :)

Just for some information, I've tried the guide in: [https://help.ubuntu.com/community/RaidConfigurationHowto?highlight=%28Raid%29](https://help.ubuntu.com/community/RaidConfigurationHowto?highlight=%28Raid%29) and I keep getting "invalid option: --o", because dmraid doesn't supports such flag... I've tried everything, please help me :(

---

### Post by DoomCypher on 2007-10-25
Bump... I'm about to give up and use mdadm... wonder if it can use raid1+0...

---

### Post by digilink on 2007-10-25
I would recommend going with mdadm. You'll need the alternate install CD. I did exactly what you are trying to accomplish with 2x250gb drives and finally gave trying to use the onboard RAID controller and used softraid instead. 

What I did was made a small partition for /boot, which I configured in RAID 1, and configured the rest for / and made those RAID 0. 

May not be what your after, but with the alternate install CD it was pretty easy. 

Hope that helps.....

---

### Post by DoomCypher on 2007-10-26
Thanks for the reply digilink :)

I've followed this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

My RAID has the same name as the raid created there, but it seems like gParted doesn't likes my new RAID5 array...

[IMG]http://img50.imageshack.us/img50/5475/screenshot1uh8.png[/IMG]

And I did:

```
mke2fs -j /dev/md0
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
183156736 inodes, 366287952 blocks
18314397 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
11179 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done.
```

But I don't seem to find either such partition name using fdisk... :confused:

```
Disk /dev/md0: 1500.3 GB, 1500315451392 bytes
2 heads, 4 sectors/track, 366287952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

What's going on? ](*,)

EDIT: well, seems like it's working?

Mounted on /ftp ..

```
/dev/md0             1442161020    202368 1368701064   1% /ftp
```

I guess I'm confused by what gPart says...

---

