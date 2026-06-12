---
title: "New Ubuntu 14.10 install and VG-Swap_1 is not ready at at Startup"
date: 2015-03-17
forum: General Help
---

### Post by brian53 on 2015-03-17
Novice Installer of Ubuntu 14.10 on an Intel WIN 7 PC.

At Bootup I see this error:

"dev/mapper/ubuntu--vg-swap_1 is not ready"

Depress S To Skip or M for Manual and if you either do nothing, or depress S or M Ubuntu DOES proceed to Logon and accessing apllications.

Thanks in advance.
Rock on :guitar:

---

### Post by nerdtron on 2015-03-17
Did you modified anything on your disks, or fstab entries before this happend?

post the output of the following commands for more troubleshooting info.
```

cat /etc/fstab
sudo blkid
lsblk
df -Th

```

---

### Post by brian53 on 2015-03-17
Thank you and here are the results of the 4 commands:
  	 	 	 	   cat /etc/fstab # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 /dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
 # /boot was on /dev/sdb1 during installation
 UUID=4fe2dae5-29be-49d6-bdad-53868bb2d19a /boot           ext2    defaults        0       2
 /dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
 /dev/mapper/cryptswap1 none swap sw 0 0
 
 
 sudo blkid
 [sudo] password for name:  
 /dev/sda1: UUID="4fe2dae5-29be-49d6-bdad-53868bb2d19a" TYPE="ext2" PARTUUID="01a123fd-01"  
 /dev/sda5: UUID="32uiNc-7Q1L-4xP4-M1KX-uwmD-aGn4-KX3rTq" TYPE="LVM2_member" PARTUUID="01a123fd-05"  
 /dev/mapper/ubuntu--vg-root: UUID="a8978cb5-9bf8-4947-92c3-c058d049e471" TYPE="ext4" 
 
 
 lsblk
 NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
 sda                     8:0    0 931.5G  0 disk  
 &#9500;&#9472;sda1                  8:1    0   243M  0 part /boot
 &#9500;&#9472;sda2                  8:2    0     1K  0 part  
 &#9492;&#9472;sda5                  8:5    0 931.3G  0 part  
   &#9500;&#9472;ubuntu--vg-root   252:0    0 925.3G  0 lvm  /
   &#9492;&#9472;ubuntu--vg-swap_1 252:1    0     6G  0 lvm   
 sr0                    11:0    1  1024M  0 rom
 
 
 _df -Th_
 Filesystem                  Type      Size  Used Avail Use% Mounted on
 /dev/mapper/ubuntu--vg-root ext4      911G  7.6G  857G   1% /
 none                        tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
 udev                        devtmpfs  2.9G  4.0K  2.9G   1% /dev
 tmpfs                       tmpfs     594M  1.1M  593M   1% /run
 none                        tmpfs     5.0M  4.0K  5.0M   1% /run/lock
 none                        tmpfs     2.9G  164K  2.9G   1% /run/shm
 none                        tmpfs     100M   48K  100M   1% /run/user
 /dev/sda1                   ext2      236M   47M  177M  21% /boot
 /home/name/.Private        ecryptfs  911G  7.6G  857G   1% /home/name

---

### Post by nerdtron on 2015-03-17
you have an fstab entry for the logical volume swap which the OS will try to mount at boot time but looking at the blkid output, you don't even have a swap UUID. 

Hmmm.. not sure about this. I hope others can give you advise.

---

### Post by brian53 on 2015-03-17
You have been most helpful identifying the problem, thank you.

---

### Post by oldfred on 2015-03-17
I do not know LVM nor encryption.

I would think it should have an UUID.

But does it have to be mounted twice, that seems like it might conflict. 

/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
 /dev/mapper/cryptswap1 none swap sw 0 0

Found this bug:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

---

