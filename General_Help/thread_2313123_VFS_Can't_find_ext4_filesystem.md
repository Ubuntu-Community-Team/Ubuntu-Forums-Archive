---
title: "VFS: Can't find ext4 filesystem"
date: 2016-02-09
forum: General Help
---

### Post by bwanaaa on 2016-02-09
IBM 160 gig HD died. On it was a dual boot installation
Windows 7 (on NTFS partition sda3)
Ubuntu server (on ext4 partition sda5)

I replaced it with a Hitachi 250 gig drive.
I restored a backup image of the drive using paragon suite 14 and amazingly all the bits seemed to be where they should on the new drive.
Fired it up and got the GRUB menu! Yay!!
Tried booting into ubuntu and at 12s into the boot process got:

```
EXT4-fs (sdb): VFS: Can't find ext4 filesystem
An error occurred while mounting /dataHN2
```

I pressed 'm' and dropped into a shell and fdisk -l gives:


```

Disk /dev/sda: a bunch of statistics
...

Device       Boot     Start            End            Blocks   Id     System
/dev/sda1                2048      114439            56196   de      Dell Utility
/dev/sda2             114688 162938879       81412096     7      HPFS/NTFS/exFAT
/dev/sda3     *  162938880 368906239     102983680     7      HPFS/NTFS/exFAT
/dev/sda4         368906240 488280063      59686912     f       W95 Ext'd (LBA)
/dev/sda5         368908288 477626367      54359040     83     Linux
/dev/sda6         477628416 488280063       5325824      82     Linux swap / Solaris


Disk /dev/sdb: a bunch of different statistics for the other drive
..
Device       Boot     Start            End            Blocks   Id     System
/dev/sdb1                2048      312498175156248064   7     HPFS/NTFS/exFAT

```

If I create a directory /tmp/mydir and mount /dev/sda5 there, I can definitley find all the files and directories of my ubuntu server
Doing:

```
cd /tmp/mydir
ls

```
gives

```
bin  boot dataHN2 dev etc.....
```

looking at /etc/fstab shows

```
# / was on /dev/sda5 during installation
UUID=a bunch of numbers and letters                 ext4   errors=remount-ro 0   1
#swap was on /dev/sda6 during installation
UUID=a different bunch of letters and numbers    swap   sw                       0   0
# /dev/sdb
/dev/sdb /dataHN2    ext3 defaults   0   0
```


So why is it choking on mounting /dataHN2? Do I need to go into a linux boot cd and reformat the other empty drive as ext4?
WEll, I did that and I still get the same error. I can still drop out of the choked boot process with 'm' and login to ubuntu server manually but I need this thing to auto boot reliably. BTW, the windows partition still works fine. I need it cause sometimes I have to stop the server to do other stuff on the LAN.

---

### Post by sandyd on 2016-02-10
There is something wrong here.

```
# / was on /dev/sda5 during installation
UUID=a bunch of numbers and letters                 ext4   errors=remount-ro 0   1
#swap was on /dev/sda6 during installation
UUID=a different bunch of letters and numbers    swap   sw                       0   0
# /dev/sdb
**/dev/sdb** /dataHN2    ext3 defaults   0   0
```

The line in fstab tries to mount /dev/sdb, which is not possible because /dev/sdb is a disk, not a partition. Going into /dev/sdb, the only partition there is a NTFS partition.

```

Device       Boot     Start            End            Blocks   Id     System
/dev/sda1                2048      114439            56196   de      Dell Utility
/dev/sda2             114688 162938879       81412096     7      HPFS/NTFS/exFAT
/dev/sda3     *  162938880 368906239     102983680     7      HPFS/NTFS/exFAT
/dev/sda4         368906240 488280063      59686912     f       W95 Ext'd (LBA)
/dev/sda5         368908288 477626367      54359040     83     Linux
/dev/sda6         477628416 488280063       5325824      82     Linux swap / Solaris


Disk /dev/sdb: a bunch of different statistics for the other drive
..
Device       Boot     Start            End            Blocks   Id     System
**/dev/sdb1 **               2048      312498175156248064   7     **HPFS/NTFS/exFAT**
```

Which partition are you trying to mount to /dataHN2 ?

---

### Post by bwanaaa on 2016-02-11
thanks. I changed the fstab to point to 

/dev/sdb1 /dataHN2    ext3 defaults   0   0

and now it boots properly and mounts the disk to dataHN2

I dont know why fstab got corrupted. The only things that changed were the actual hard drives. Maybe the fstab is tied to a specific drive identifier and when it sees a new drive it chokes?

Anyway, now I have to figure out why my restored drive is not seeing the network. Another weird change. Or perhaps I made the backup before I set the network settings.
EDIT: found out that the *new* ethernet card (new to the OS because it was used to seeing a different EthernetMAC address) was assigned to eth1

---

