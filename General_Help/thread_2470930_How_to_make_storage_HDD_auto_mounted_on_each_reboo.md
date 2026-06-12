---
title: "How to make storage HDD auto mounted on each reboot"
date: 2022-01-17
forum: General Help
---

### Post by satimis on 2022-01-17
Just add an old 2TB WD hdd on a spare PC.

Run fdisk to delete all partitions creating single parition on it

Run
$ sudo mkfs.ext4 /dev/sdb

On reboot PC the old 2TB WD hdd can't be mounted automatically.

$ lsblk -o NAME,FSTYPE,UUID ```

NAME                FSTYPE      UUID
loop0               squashfs    
loop1               squashfs    
loop2               squashfs    
loop3               squashfs    
loop4               squashfs    
loop5               squashfs    
loop6               squashfs    
loop7               squashfs    
loop8               squashfs    
loop9               squashfs    
loop10              squashfs    
loop11              squashfs    
loop12              squashfs    
sda                             
&#9500;&#9472;sda1              vfat        CC6D-6E39
&#9492;&#9472;sda2              LVM2_member WLJcOs-IsZN-P1Vp-tG1n-nmGt-BQaI-2BF9EI
  &#9500;&#9472;vgubuntu-root   ext4        08318952-af08-469d-9d06-7228d3c75e49
  &#9492;&#9472;vgubuntu-swap_1 swap        72cfa635-c7a4-4bed-8f04-538b801bf712
sdb                 ext4        67dc28ae-a823-469c-a23c-7434b38be0de
sr0                             

```

$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CC6D-6E39  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgubuntu-swap_1 none            swap    sw              0       0

```

Please advise how to make the old 2TB WD hdd mounted r,w automatically on each reboot ?

Thanks

Regards

---

### Post by LuddDjur on 2022-01-17
you could do something like this (assuming you want to mount it to /mnt)

```
sudo -i 
echo "UUID=67dc28ae-a823-469c-a23c-7434b38be0de  /mnt  ext4 errors=remount-ro 0  0" >> /etc/fstab
```

means.. mount partition with this uuid to /mnt as type ext4, remount as readonly if errors occur, 0 for do not backup/dump this mountpoint, and 0 for do not check filesystem for boot (pass)

---

### Post by satimis on 2022-01-17
> **LuddDjur said:**
> you could do something like this (assuming you want to mount it to /mnt)

```
sudo -i 
echo "UUID=67dc28ae-a823-469c-a23c-7434b38be0de  /mnt  ext4 errors=remount-ro 0  0" >> /etc/fstab
```

means.. mount partition with this uuid to /mnt as type ext4, remount as readonly if errors occur, 0 for do not backup/dump this mountpoint, and 0 for do not check filesystem for boot (pass)
Thanks for your advice.

Performed following steps on Terminal;

$ sudo -i
[sudo] password for satimis: 

root@PC2A:~# echo "UUID=67dc28ae-a823-469c-a23c-7434b38be0de  /mnt  ext4 errors=remount-ro 0  0" >> /etc/fstab
no complaint

Reboot PC

-> File Manager -> Other Locations.

The WD HDD is not displayed there.  What is PC2A ? I have no another PC running on the Network

I have to explain more about the history of this PC

There are 4 hdds on this PC

hdd-1 2TB ssd running Ubuntu 20.04 which have been running on this PC for prolonged time
hdd-2 2TB WD hdd installed together with hdd-1, solely for data storage. ext 4 format

hdd-3 500G ssd, recently added, running Windows 10
hdd-4 250G ssd, also recently added, running Ubuntu 20.04.

hdd-5 2TB WD hdd, an old hdd just added having data on it, ext 4 format but without OS.

I unplug hdd-1, hdd-2 and hdd-3 to avoid confusion to run fdisk on hdd-4 creating single partition on hdd-5.


Regards

---

### Post by satimis on 2022-01-17
Hi all,

Problem solved.  Steps performed on Terminal as follows;

$ sudo fdisk -l | grep sdb```

Disk /dev/sdb: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors

```

$ sudo blkid | grep sdb```

/dev/sdb: UUID="67dc28ae-a823-469c-a23c-7434b38be0de" TYPE="ext4"
```

$ sudo mkdir /data
$ sudo groupadd data
$ sudo usermod -aG data satimis
$ sudo chown -R :data /data

$ sudo nano /etc/fstab 
Comment out following line
UUID=67dc28ae-a823-469c-a23c-7434b38be0de  /mnt  ext4 errors=remount-ro 0  0
Add following line
UUID=67dc28ae-a823-469c-a23c-7434b38be0de /data    auto nosuid,nodev,nofail,x-gvfs-show 0 0
Save and Exit

$ sudo mount -a
The old WD hdd mounted
screenshot_folder_empty.png

$ reboot
File Manager -> Other Locations
The old WD hdd is there. 
But the permission is READ only

$ ls -ald /data/```

drwxr-xr-x 3 root root 4096 Jan 17 22:52 /data/

```

$ sudo chown satimis:satimis -R /data

Now the old WD hdd is read and write.

Reconnect all cables and boot.  The original WD hdd is also there

Now the PC is working as normal.

Thanks

Regards

---

### Post by Impavidus on 2022-01-17
Some tools may have been confused as you created the filesystem directly on the drive, not in a partition.

---

### Post by satimis on 2022-01-17
> **Impavidus said:**
> Some tools may have been confused as you created the filesystem directly on the drive, not in a partition.
I use the entire hdd for storage only, no partition on this disk

---

