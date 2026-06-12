---
title: "RAID array doesn't assemble after reboot."
date: 2016-12-12
forum: General Help
---

### Post by andrew-000 on 2016-12-12
RAID array doesn't assemble after reboot.


I have one SSD from which the system is booted, and three HDD that are part of the array. The system is Ubuntu 16.04.


The steps that I've followed are based mostly on this guide:


[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-5-array)


1. Verifying if I'm good to go.


```
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
```


The output shows sda, sdb, and sdc devices besides the SSD partitions. I've verified if these in fact represent HDDs by looking at output of this: 


```
hwinfo --disk
```


Everything matches.


2. Assembling the array.


```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc
```




I verify if it looks OK by entering: ```
cat /proc/mdstat
```


The output looks something like this:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc[3] sdb[1] sda[0]
      7813774336 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      [=======>.............]  recovery = 37.1% (1449842680/3906887168) finish=273.8min speed=149549K/sec
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>

```


I wait till the process ends.
```

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc[3] sdb[1] sda[0]
      209584128 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]


unused devices: <none>

```
3. Creating and mounting the filesystem.
```

sudo mkfs.ext4 -F /dev/md0


sudo mkdir -p /mnt/md0


sudo mount /dev/md0 /mnt/md0


df -h -x devtmpfs -x tmpfs

```
I put some data in, and the output looks like this:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2  406G  191G  196G  50% /
/dev/nvme0n1p1  511M  3.6M  508M   1% /boot/efi
/dev/md0        7.3T  904G  6.0T  13% /mnt/md0

```
4. Saving the array layout.
```

sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf


sudo update-initramfs -u


echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab

```
5. Rebooting and verifying if everything works correctly.


After reboot I try: 
```
cat /proc/mdstat
```
It isn't showing any active raid devices. 


```
ls /mnt/md0
``` 


is empty.


The following command isn't printing anything and doesn't work either:
```

mdadm --assemble --scan -v

```


Only the following restores the array with data on it: 


```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc
```




What should have been done differently?


Is it related to the output of this?


```
sudo dpkg-reconfigure mdadm
```


The output shows:
```

update-initramfs: deferring update (trigger activated)
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Adding boot menu entry for EFI firmware configuration
done
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic

```


The intriguing part for me is "start and stop actions are no longer supported; falling back to defaults"




Also the output of ```
/usr/share/mdadm/mkconf
``` doesn't print any arrays at the end.
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR craftinity@craftinity.com


# definitions of existing MD arrays

```


whereas the output of ```
cat /etc/mdadm/mdadm.conf
``` does.


```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# DEVICE /dev/sda /dev/sdb /dev/sdc


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR craftinity@craftinity.com


# definitions of existing MD arrays


# This file was auto-generated on Sun, 04 Dec 2016 18:56:42 +0100
# by mkconf $Id$


ARRAY /dev/md0 metadata=1.2 spares=1 name=hinton:0 UUID=616991f1:dc03795b:8d09b1d4:8393060a

```

---

