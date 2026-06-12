---
title: "converting from Raid1 to LVM; moving to a different parition"
date: 2014-08-02
forum: General Help
---

### Post by ajonen on 2014-08-02
I am in process of converting from a riad1 setup to an lvm setup.
step 1 for me is going to be going from md0 to md1.
I didn't see a real good tutorial online so i figured i would write down my steps for future usage.
I will continue to update as i go along.

STEP1.  Go from MD1 (root) to MD0 (100G swap drive)

1. my setup 
64 bit ubuntu server 12.10 LTS
Physical:
/dev/sda
    /dev/sda1 - 100G  primary
    /dev/sda2 - 1.8TB Primary bootable
/dev/sdb
    /dev/sdb1 - 100G primary
    /dev/sdb2 - 1.8TB Primary bootable

Raid - software:
/dev/md0
    /dev/sda1
    /dev/sdb1

/dev/md1
    /dev/sda2
    /dev/sdb2

/ is mounted to /md0
I do not have a separate parition for boot or home
I did have a separate parition for swap that was 100 gig.  So i am using
that as a place holder to add lvm onto /dev/md0

In my case /md0 was the new partition and md1 was the old partition;
In the end i am going to add an lvm to md1 and transfer again to that.

######################################3
# turn off swap and format as ext4
####################################3
from original system lets turn off the swap;

1. ```
swapoff -a
```;
there are many ways to create a new swap later if needed.
see:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
comment out the swap parition from /etc/fstab
     vi /etc/fstab;


2.  create a swap file instead
     ```
sudo dd if=/dev/zero of=/mnt/512MiB.swap bs=1024 count=524288;
     sudo chmod 600 /mnt/512MiB.swap;
sudo mkswap /mnt/512MiB.swap;
sudo swapon /mnt/512MiB.swap
```


to make the change permanent:
add this line to /etc/fstab and save the file

     ```
/mnt/512MiB.swap  none  swap  sw  0 0
```

2. format the swap parition as 
```
      mkfs.ext4 /dev/md0
```

############################
# move to new parition (old swap partition)
#########################
1. install ubuntu 12.10 onto a bootable live usb and boot to it.
click try ubuntu
bring up a terminal session

2.
```
     sudo su;
```

3. install support for software raid so we can see the raid drives:
```
        sudo apt-get install mdadm;
```

4. setup raid 
```
        sudo mdadm --assemble --scan;
```
verify the drives are ready

```
      cat /proc/mdstat;
```
you should see your two drives ready

5.
```
     sudo fdisk -l;
```
    this will show current partition; verify old and new paritions

6. mount old parition
```
      mkdir /mnt/old
     mount /dev/md1 /mnt/old
```

7. mount new partition
```
      mkdir /mnt/new
     mount /dev/md0 /mnt/new
```

8. copy the old parition to the new parition preserving 
file ownership;

```
 cp -axpf /mnt/old /mnt/new/;
```

this step may take a while

9. edit fstab for new UUID for /dev/md0
a. verify blkid 

```
      blkid > blockid.txt;
```

b. open blockid.txt  with a text editor and copy the blkid for md0
```
      vim blockid.txt;
```
copy text

make sure you are in the new mount point
c. 
```
    vim  /mnt/new/etc/fstab;
```
we could comment out line for original disk so we do not lose it.
replace the UUID with the one obtained previously.
mine ended up looking like this with line numbers on the left:

1 ## /etc/fstab: static file system information.
 2 #
 3 # Use 'blkid' to print the universally unique identifier for a
 4 # device; this may be used with UUID= as a more robust way to name devices
 5 # that works even if disks are added and removed. See fstab(5).
 6 #
 7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 8 proc            /proc           proc    nodev,noexec,nosuid 0       0
 9 # / was on /dev/md1 during installation
10 UUID=7721c749-f8ef-4f48-96d6-5fd49b977059 /               ext4    errors=remo
11 # swap was on /dev/md0 during installation
12 #UUID=9cd01b16-9a28-4c54-829c-8b14c0b22e9e none            swap    sw   


10. now to install and update grub
bind mount /dev /dev/pts /proc /sys to your new systems mount point;
this will allow chroot
```
     mount -B /dev /mnt/new/dev
    mount -B /dev/pts /mnt/new/dev/pts
    mount -B /proc /mnt/new/proc
    mount -B /sys /mnt/new/sys
```

11. chroot into the new system.  commands run now are run as if in 
the new partition.
```
     sudo chroot /mnt/new;
```

12. Install new grub as if from new partition onto both 
physiscal devices
```

     sudo grub-install /dev/sda;
     sudo grub-install /dev/sdb;

```
13. recreate grub menu;
     ```
sudo grub-update

```
14. exit from chroot and reboot
     ```
exit;
     reboot;

```
make sure to pull out the live usb before reboot.

############################ 
#boot to your new install and create lvm on /dev/md1
############################3
1. ```
apt-get install lvm2
```
2. create volume group
```
vgcreate vg0 /dev/md1
``` (md1 is the old install)
3. create root parition
```
lvcreate -L 200G -n vg0-root vg0 
```
4. create swap parition
```
lvcreate -L 10G -n vg0-swap vg0 
```
5. format root parition
```
mkfs.ext4 /dev/mapper/vg0-root
```
*be carefull here once you do this the disk is formatted
6. format swap parition
```
mkswap /dev/mapper/vgswap

```
#######################33
# converting to lvm
############################

1. boot from live usb

2. install support for software raid so we can see the raid drives:
```
        sudo apt-get install mdadm;
```

3. setup raid 
```
        sudo mdadm --assemble --scan;
```
verify the drives are ready

4. ```
# apt-get install lvm2
```
 
5. To make sure the harddisk is recognised, you can use fdisk
```
fdisk -lu
```
 
6. Once installed, run pvscan to scan all disks for physical volume. this to make sure your LVM harddisk is detected by Ubuntu
```
 pvscan
```
PV /dev/sda2 VG VolGroup00 lvm2 [74.41 GB / 32.00 MB free]
Total: 1 [74.41 GB] / in use: 1 [74.41 GB] / in no VG: 0 [0 ]
 
 
7. After that run vgscan to scan disks for volume groups.
```
# vgscan
```
Reading all physical volumes. This may take a while...
found ....
 
 
8. Activate all volume groups available.
```
 vgchange -a y
```
2 logical volume(s) in volume group "Vg0"
 
9. Run lvscan to scan all disks for logical volume. You can see partitions inside the hard disk now active.
```
 lvscan
```

 
10. Mount the partition to any directory you want, usually to /mnt
```
 mount /dev/mapper/vg0-root /mnt/new
```
 

Now simply follow the same process as above when we moved from the raid1 to the swap.  Only this time you need to mount the new lvm, copy everything over, and setup grub, install grub to the mbr.

 





references:
[URL="http://askubuntu.com/questions/20460/move-installation-to-new-disk"]http://linuxlov3r.blogspot.com/2012/05/creating-swap-partition-in-lvm.html
http://askubuntu.com/questions/20460/move-installation-to-new-disk[/URL]
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)

---

