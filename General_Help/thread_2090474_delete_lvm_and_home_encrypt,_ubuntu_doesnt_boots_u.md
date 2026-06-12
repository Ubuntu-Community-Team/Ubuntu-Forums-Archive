---
title: "delete lvm and home encrypt, ubuntu doesnt boots up"
date: 2012-12-02
forum: General Help
---

### Post by salar moghaddam on 2012-12-02
for first i have really really important things in my hard and i dont want to lost them
for secound time,my english is very bad :D
i was set lvm and home encrypting in ubuntu installation
today i wanted to have another partition for installing windows
i used gparted in live cd and it couldnt resize partitions because partitions had lvm 
i used this topic [http://tcpdump.com/kb/os/linux/lvm-removal.html](http://tcpdump.com/kb/os/linux/lvm-removal.html) to remove lvm 
i could unlock the sda1 and sda2 partitions but the sda5 partition not unlocked
sda 5 for lvm named luks-c9ffb771-14dc-4b6c-8793-6654b5621e10
my partitions info :
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003e974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1465147391   732322816   83  Linux

Disk /dev/mapper/luks-c9ffb771-14dc-4b6c-8793-6654b5621e10: 749.9 GB, 749896466432 bytes
255 heads, 63 sectors/track, 91169 cylinders, total 1464641536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/luks-c9ffb771-14dc-4b6c-8793-6654b5621e10 doesn't contain a valid partition table

```and gparted :
[[IMG]http://uploadimage.ir/uploads/thumbs/13544690061.png[/IMG]]("http://uploadimage.ir/")
[http://uploadimage.ir/uploads/13544690061.png](http://uploadimage.ir/uploads/13544690061.png)
i tried :
```
mount /dev/mapper/luks-c9ffb771-14dc-4b6c-8793-6654b5621e10 /mnt
``` but terminal answer :
```
mount: unknown filesystem type 'LVM2_member'
```then i typed 
```
lvremove /dev/mapper/luks-c9ffb771-14dc-4b6c-8793-6654b5621e10 
```and it answered :
```
 skip_dev_dir: Couldn't split up device name luks-c9ffb771-14dc-4b6c-8793-6654b5621e10
  Volume group "luks-c9ffb771-14dc-4b6c-8793-6654b5621e10" not found
  Skipping volume group luks-c9ffb771-14dc-4b6c-8793-6654b5621e10
```then i rebooted my laptop and it didnt boot
when the ubuntu boots it request me the lvm pass and i entered that but it didnt boot
i asked my best friend ( google :D ) and he answered this topic [http://ubuntuforums.org/showthread.php?t=868681](http://ubuntuforums.org/showthread.php?t=868681)
my sda5 partition information is :
```

sudo cryptsetup luksDump /dev/sda5
LUKS header information for /dev/sda5

Version:           1
Cipher name:       aes
Cipher mode:       xts-plain64
Hash spec:         sha1
Payload offset:    4096
MK bits:           512
MK digest:         b9 15 74 37 ab 04 f8 82 c7 1b b6 2c 50 8a 5b 10 1a 68 74 45 
MK salt:           47 d3 95 20 a5 16 8e f7 dc e9 1f 64 84 4f 79 59 
                   8b 29 7d 8e 2b c6 ae b5 63 79 f0 5d 8a 72 01 b0 
MK iterations:     52625
UUID:              c9ffb771-14dc-4b6c-8793-6654b5621e10

Key Slot 0: ENABLED
    Iterations:             210834
    Salt:                   4b 3c 1a 3c 14 a5 eb 14 b9 f8 9a 38 10 68 87 ba 
                              59 fe d1 bb f5 56 74 52 79 bc e4 08 02 20 83 f7 
    Key material offset:    8
    AF stripes:                4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED


```i tried :
```
sudo cryptsetup luksOpen /dev/sda5 /mnt
```then i entered my pass and then it answered :
```
Cannot use device /dev/sda5 which is in use (already mapped or mounted).
```but it isnt mounted!
```
ls /dev/mapper
control  luks-c9ffb771-14dc-4b6c-8793-6654b5621e10
``````
root@ubuntu:~# mount /dev/sda5 /dev/mapper/test
mount: unknown filesystem type 'crypto_LUKS'
```i did anything in that topic and no one help me :(
i dont know what to do :(
please help me i need my files :(

---

### Post by dino99 on 2012-12-02
everytime you tweak a partition, it get a new uuid, explaining grub still have the old ones, and so cant boot.
what you need to do: boot on a livecd, open a terminal, and reinstall grub:

```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by salar moghaddam on 2012-12-02
> **dino99 said:**
> everytime you tweak a partition, it get a new uuid, explaining grub still have the old ones, and so cant boot.
what you need to do: boot on a livecd, open a terminal, and reinstall grub:

```
sudo grub-install /dev/sda
sudo update-grub
```

i need just unlock the sda5 partition to install windows then i will have to install grub again now its better to unlock the sda5

---

### Post by Cheesemill on 2012-12-02
If you've followed the link in your first post to remove LVM than you have effectively deleted the partition that contains all of your data. Even if you do manage to unlock your encrypted sda5 partition you have deleted the underlying LVM logical volume.

The easiest thing to do would just be to wipe your drive, install windows, then install Ubuntu, then restore all of your data from a backup.

---

### Post by haqking on 2012-12-02
> **Cheesemill said:**
> 

  then restore all of your data from a backup.

you know what is coming dont you ?....lets see how "important" that data was ;-)

---

### Post by salar moghaddam on 2012-12-02
i wanted to recovery the grub
i boot up from livecd and the opened the terminal and :
```
sudo su
mount / /mnt
rm -r /mnt/boot
mkdir boot
mount dev/sda1 /mnt/boot
grub-install --root-directory=/mnt/ /dev/sda
```
grub was installed (i mounted / (root cd) because i dont have the root partition (sda5 locked) and the boot partition unlocked , i used that for boot to install and update grub)
then i wanted chroot to update grub
```
chroot /mnt
bash 4.2 #update-grub
update-grub not found
apt-get install grub
apt-get not found
```
:|
why?

---

### Post by Cheesemill on 2012-12-03
I am not sure why you tried to re-install grub when this wasn't the problem.

The problem is that you have completely deleted your root partition which contained your OS and its data.

You have 2 options - Either reinstall the OS and restore your data from a backup or try and recover what's left of your old root partition.

To attempt recovery you would have to boot from a Live CD, then unlock sda5 using 'sudo cryptsetup luksOpen /dev/sda5', then install testdisk on the running live system and use it on the /dev/mapper/luks* device to see if anything can be salvaged. You will probably need a spare hard drive with as much space as the deleted partition had to perform the recovery.

Moral of the story - don't follow a guide that tells you how to remove partitions and then wonder where your partitions have gone.

---

