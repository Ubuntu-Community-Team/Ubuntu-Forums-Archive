---
title: "Mounting problem"
date: 2019-12-01
forum: General Help
---

### Post by Alligator on 2019-12-01
I'm trying to mount a 6TB usb drive using this process [https://linuxconfig.org/howto-mount-usb-drive-in-linux](https://linuxconfig.org/howto-mount-usb-drive-in-linux). It's supposedly mount according to the instructions; however, when running the back-up script - error - external back up drive not mounted.  Here's some info.

Help would be greatly appreciated.  Thanks in advance.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=ba1ded83-00f0-4bd5-8abf-6f8465db86a1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7BEA-8267  /boot/efi       vfat    umask=0077      0       1

# External usb-drive for backups
UUID=BBA1524E-D507-40B8-9FC0-F7B007559DEB /media/usb-drive ext4 user,noauto,rw 0 0

/swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/E52C-9AFC /mnt/E52C-9AFC auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/47b89303-7511-4a80-bfa7-8cb91a791eda /mnt/47b89303-7511-4a80-bfa7-8cb91a791eda auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/ae1a14ef-0d82-42a7-9e36-09e693555476 /mnt/ae1a14ef-0d82-42a7-9e36-09e693555476 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Data 0 0
/dev/disk/by-uuid/93d37b7c-55f5-413f-b375-e54563dd883b /media/usb-drive/93d37b7c-55f5-413f-b375-e54563dd883b  /media/usb-drive ext4 0 0


```

```

The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 5.5 TiB, 6001175125504 bytes, 11721045167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: BBA1524E-D507-40B8-9FC0-F7B007559DEB

Device      Start         End     Sectors  Size Type
/dev/sdc1      34      262177      262144  128M Microsoft reserved
/dev/sdc2  264192 11721043967 11720779776  5.5T Microsoft basic data

Partition 1 does not start on physical sector boundary.

```

```

ls -l /dev/disk/by-uuid/*
lrwxrwxrwx 1 root root 10 Dec  1 11:10 /dev/disk/by-uuid/273f2d3b-f251-68fc-5404-7de28cce4232 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Dec  1 11:10 /dev/disk/by-uuid/7BEA-8267 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec  1 15:58 /dev/disk/by-uuid/93d37b7c-55f5-413f-b375-e54563dd883b -> ../../sdc1
lrwxrwxrwx 1 root root 10 Dec  1 16:05 /dev/disk/by-uuid/94BA918FBA916F0C -> ../../sdc2
lrwxrwxrwx 1 root root 10 Dec  1 11:10 /dev/disk/by-uuid/ae1a14ef-0d82-42a7-9e36-09e693555476 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Dec  1 11:10 /dev/disk/by-uuid/ba1ded83-00f0-4bd5-8abf-6f8465db86a1 -> 

```

The backup script
```

#!/bin/sh
#
#
# This is a backup script from The Computer Clinic
# Please run this with the sudo command!!!

 
location=/*
# destination=
destination=/media/usb-drive/93d37b7c-55f5-413f-b375-e54563dd883b

echo
echo "ATTENTION: Please run using the sudo command. exp sudo ~/usb_backup_script.sh"

while :
do
        if [ -d $destination ]
        then
                break
        else

                echo
                echo "The Linux Backup external drive is not mounted, please investigate"               
                read junk
               exit 1
        fi
done

#       rsync -axz --dry-run --delete --exclude=/proc --exclude=/sys \
#                                        --exclude=/mnt --exclude=/media \
#
# Use --dry-run to simulate cmd and use --log-file=/tmp/backupshit.txt to check for errors

        rsync -rltDvu --progress --delete --delete-excluded --exclude-from=backup.lst \
        $location $destination

        echo "Changing Permission, please wait..."
        chown -R ron:ron $destination

```

```

/media/usb-drive$ ls 
 lost+found  'Seagate Backup Plus Drive'

```

---

### Post by oldfred on 2019-12-01
You first need to repair gpt partition table. And it looks like partition is not ext4, but created by Windows so NTFS?
You seem to have multiple UUIDs in fstab or script that do not exist, you have to use the UUID of sdc2 or whatever partition you want to use on sdc.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

Check partitions & formats.
sudo parted /dev/sda unit s print 

Check UUIDs:
      
 sudo blkid -c /dev/null -o list 
lsblk -f

Make sure fstab only has UUIDs shown above.
cat /etc/fstab
if changes required:
sudoedit /etc/fstab

I prefer to label all partitions, and use mounts that have some meaning. My backup partition is labeled backup & mounted at /mnt/backup. Do not mix those as really different. I have labeled data and mounted as /mnt/data and had issues. New gpt partition have two labels one for GUID/gpt and one for partitioning. And just to confuse things gpt or MBR(msdos) is also called a partitioning label.

One of my drives that has a fewer number of partitions:
```
       

 fred@bionic-z97:~$ lsblk -f
NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
sdc                                                          
&#9500;&#9472;sdc1  vfat   ESP_C    A124-26A6                            
&#9500;&#9472;sdc2                                                       
&#9500;&#9472;sdc3  ext4   rootc    f0740999-017f-4a68-9f97-6af9960f497c 
&#9500;&#9472;sdc4  ext4   backup_c e03e432e-6b3a-40e7-92dc-ffda559c4693 /mnt/backupC
&#9492;&#9472;sdc5  ext4   old_data cffe5249-4cac-4f99-8271-186d48464d3e  
    
```

---

### Post by Morbius1 on 2019-12-02
You have another problem:
> /dev/disk/by-uuid/93d37b7c-55f5-413f-b375-e54563dd883b /media/usb-drive/93d37b7c-55f5-413f-b375-e54563dd883b  /media/usb-drive ext4 0 0

The form of an fstab partition declaration is:
[DEVICE] [MOUNT POINT] [FILESYSTEM TYPE] [MOUNT OPTIONS] [DUMPED FREQ] [FS CHECK]

The system will read that entry from left to right and when it encounters a blank it will signal the end of one field and the beginning of the next.

In your case:
[DEVICE] = /dev/disk/by-uuid/93d37b7c-55f5-413f-b375-e54563dd883b
[MOUNT POINT] = /media/usb-drive/93d37b7c-55f5-413f-b375-e54563dd883b
[COLOR=#0000cd][B][FILESYSTEM TYPE] = /media/usb-drive
[MOUNT OPTIONS] = ext4
[/B][/COLOR]
[COLOR=#0000cd] The highlighted entries above are incorrect.[/COLOR]

I think what you meant to enter was:
```
/dev/disk/by-uuid/93d37b7c-55f5-413f-b375-e54563dd883b /media/usb-drive/93d37b7c-55f5-413f-b375-e54563dd883b  ext4 defaults 0 0
```

---

