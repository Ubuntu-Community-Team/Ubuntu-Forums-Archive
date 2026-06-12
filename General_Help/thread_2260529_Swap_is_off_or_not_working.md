---
title: "Swap is off or not working"
date: 2015-01-12
forum: General Help
---

### Post by Evil Wayz on 2015-01-12
Noticed when I went to system monitor that my swap is off.  Used gparted to turn it back on but it still doesn't seem to be doing anything.  I have 8 gb of ram so I'm not sure if this is a big deal or not.  Also when I reboot have to turn it back on again.

---

### Post by egeezer on 2015-01-12
Gparted has a swapon/swapoff option - does yours show up there?

---

### Post by Impavidus on 2015-01-12
With 8GB ram you don't really need swap, but it might be good to have a little. Is the swap partition correctly listed in /etc/fstab?

---

### Post by Evil Wayz on 2015-01-12
> **Impavidus said:**
> With 8GB ram you don't really need swap, but it might be good to have a little. Is the swap partition correctly listed in /etc/fstab?

I dunno here it is:

[IMG]http://i62.tinypic.com/a3nk0n.png[/IMG]

---

### Post by buzzingrobot on 2015-01-12
I don't see in my System Monitor an indicator that says swap is on or off.

You have a swap partition in your /etc/fstab file, as you should.  Executing 'swapon --show' in a terminal will return the device name, size, and amount used of the swap partition.  Executing 'free' in a terminal will also display the size of the swap partition and the amount in use.

It's not unusual for zero bytes of the swap partition to be in use.  Swap is used when something requests an allocation of RAM that's greater than the amount of RAM that's available at that point. (That's simplistic, but that's the general way it works.) Unless a program requests the OS to give it X bytes of RAM when something less that X bytes are available, then you won't see swap being used.

---

### Post by Evil Wayz on 2015-01-12
This is what it looks like when I reboot: [IMG]http://i58.tinypic.com/icobgl.jpg[/IMG]

Ok screw this, I'll post a picture tomorrow when I can internet again.

---

### Post by plucky on 2015-01-13
Post output for ```
sudo blkid
``` and compare the UUID for the swap partition with the value given in /etc/fstab.

It has to be the same.

Change the value in /etc/fstab if they are different.

For example ```
from sudo blkid
/dev/sda5: UUID="fd949fc4-2a51-45d8-913e-f690352f4a50" TYPE="swap" 

from /etc/fstab
# swap was on /dev/sda5 during installation
UUID=fd949fc4-2a51-45d8-913e-f690352f4a50 none            swap    sw  
```

Good Luck

---

### Post by HermanAB on 2015-01-13
Howdy,

Swap is described in the swapon man page.  It is a very good man page, so do yourself a favour and read:
$ man swapon

---

### Post by Evil Wayz on 2015-01-17
> **plucky said:**
> Post output for ```
sudo blkid
``` and compare the UUID for the swap partition with the value given in /etc/fstab.

It has to be the same.

Change the value in /etc/fstab if they are different.

For example ```
from sudo blkid
/dev/sda5: UUID="fd949fc4-2a51-45d8-913e-f690352f4a50" TYPE="swap" 

from /etc/fstab
# swap was on /dev/sda5 during installation
UUID=fd949fc4-2a51-45d8-913e-f690352f4a50 none            swap    sw  
```

Good Luck


Ok now I followed this to the letter, and when I rebooted, it said disk drive in /etc/fstab is not present, so I hit skip mounting, computer booted up fine, logged in and pulled up system monitor and it shows swap as on, but 3.4 gigs, which is not the correct size.  Everything appears to be running fine, but that error message after GRUB concerns me.  So what did I do wrong?

---

### Post by plucky on 2015-01-18
> Ok now I followed this to the letter, and when I rebooted, it said disk drive in /etc/fstab is not present, so I hit skip mounting, computer booted up fine, logged in and pulled up system monitor and it shows swap as on, but 3.4 gigs, which is not the correct size. Everything appears to be running fine, but that error message after GRUB concerns me. So what did I do wrong? 

Open a terminal and post output for ```
sudo blkid
cat /etc/fstab
sudo fdisk -l
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by Evil Wayz on 2015-01-18
sudo blkid:
```
/dev/sda1: UUID="e8e318f8-e227-4920-9adc-8362b2cf72e0" TYPE="ext4" 
/dev/sda2: UUID="816d36ac-98af-4a51-bf2b-f2e09a34ae15" TYPE="swap" 
/dev/sdb1: UUID="2a1e3aba-3972-4747-8794-cb8a38caf061" TYPE="ext4" 
/dev/sdb5: UUID="eff96e94-e511-4293-98fd-3138dc983071" TYPE="swap" 
/dev/sdc1: LABEL="My Passport" UUID="EE80FFE980FFB665" TYPE="ntfs" 

```

cat /etc/fstab :
```
UUID="eff96e94-e511-4293-98fd-3138dc983071eff96e94-e511-4293-98fd-3138dc983071# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e8e318f8-e227-4920-9adc-8362b2cf72e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eff96e94-e511-4293-98fd-3138dc983071 none            swap    sw              0       0

```

sudo fdisk -l :
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e5c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    75194367    37596160   83  Linux
/dev/sda2        75194368    78163967     1484800   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00026708

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3899959295  1949978624   83  Linux
/dev/sdb2      3899961342  3907028991     3533825    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5      3899961344  3907028991     3533824   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3906963455  1953480704    7  HPFS/NTFS/exFAT

```

cat /etc/initramfs-tools/conf.d/resume :
```
RESUME=UUID=6ad93b0f-105a-42bf-8981-2ac37164d408

```

---

### Post by plucky on 2015-01-18
```
UUID="eff96e94-e511-4293-98fd-3138dc983071eff96e94-e511-4293-98fd-3138dc983071
```

That part of the line should not be in the /etc/fstab file.

You have two swap files and you used the swap file on the two Terabyte drive,that is why the size is different.Try changing it to the swap partition on sda drive.

> RESUME=UUID=6ad93b0f-105a-42bf-8981-2ac37164d408

```
sudo nano /etc/initramfs-tools/conf.d/resume
```

Also change that value to the UUID of the swap partition you are using in /etc/fstab file so that hibernation should work.

What is installed on Sdb drive?

---

### Post by Evil Wayz on 2015-01-18
So edit fstab so the swap file sda2 is the one being used? And change the resume file to what you show above?

I have linux mint 17 on the big drive

---

### Post by plucky on 2015-01-19
> **Evil Wayz said:**
> So edit fstab so the swap file sda2 is the one being used? And change the resume file to what you show above?

I have linux mint 17 on the big drive

/etc/fstab should look like ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e8e318f8-e227-4920-9adc-8362b2cf72e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=816d36ac-98af-4a51-bf2b-f2e09a34ae15 none            swap    sw              0       0
```

and /etc/initramfs-tools/conf.d/resume should look like ```
RESUME=UUID=816d36ac-98af-4a51-bf2b-f2e09a34ae15
```

Good Luck

---

