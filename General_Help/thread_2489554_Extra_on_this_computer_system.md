---
title: "Extra on this computer system"
date: 2023-08-02
forum: General Help
---

### Post by jgw on 2023-08-02
I have a problem in that the system doesn't think I have something.  The fact is that it shows me two of the same thing.  There are two pictures.  One from Discs shows what is real, the other one show two.  

I have no idea what to do about this one..................

---

### Post by SeijiSensei on 2023-08-02
The image on the right shows a USB stick and three different hard drives. There are 3 TB and 4 TB Hitachis, and a 4 TB Western Digital. I don't know what the image on the left is supposed to show since I don't use vanilla Ubuntu.

Open a terminal and enter
```
sudo fdisk -l
```

If it says fdisk isn't installed, run 
```
sudo apt install fdisk
```
then the command above.

It will list all the storage devices on the machine.

---

### Post by jgw on 2023-08-03
Thank you for the reply....

There were 2 pictures.  One was from the Disks program and showed 3 hard drives.  The second was Nautilus (files) list of other sources available.  That one shows 4 source drives.  The last two have the same name (3tb)  and hold the same items and both are the same drive.

Its interesting.  I clicked on the one that shouldn't be there and nautilus(files) asked me if I wanted to unmount it.  I tried and failed.  Basically, because its not really mounted! (according to disks)  So, I currently can't get it changed.  What I can do is disconnect the last one and re-boot that might do the trick but I thought I had better ask before I did anything else.  

Your suggestion shows my ssd (boot, etc), and 3 hard drives.  my nautilus (files) thinks there are two exactly the same).  

Here is the results of your suggestion:
[HTML]
greg@greg2:~$ sudo fdisk -l
[sudo] password for greg: 
Disk /dev/loop0: 73.86 MiB, 77443072 bytes, 151256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 53.26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: SanDisk SDSSDH31
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4FCA70C6-1531-4F56-A873-AC5D320217D5

Device       Start        End    Sectors   Size Type
/dev/sda1     2048       4095       2048     1M BIOS boot
/dev/sda2     4096    1054719    1050624   513M EFI System
/dev/sda3  1054720 2000408575 1999353856 953.4G Linux filesystem


Disk /dev/sdb: 2.73 TiB, 3000592982016 bytes, 5860533168 sectors
Disk model: Hitachi HUA72303
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 406021F5-4ABC-436D-A69F-3166EE0F7913

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 5860532223 5860530176  2.7T Linux filesystem


Disk /dev/sdc: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WD4000FYYX      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 93D2DCDC-D797-4536-943D-17C84948A486

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.6T Linux filesystem


Disk /dev/sdd: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: HITACHI HUS72404
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 17FCBD10-AEC1-496D-B439-A479DBA711D3

Device     Start        End    Sectors  Size Type[/HTML]

---

### Post by SeijiSensei on 2023-08-03
/dev/sdd exists, but it is not partitioned nor formatted. Use
```
sudo fdisk /dev/sdd
```
then "n" to create a new partition. Accept the defaults so it consumes the entire drive. Then enter "w" to write the new partition table to the device.

You'll then need to format the new partition like this
```
sudo mkfs -t ext4 /dev/sdd1
```

Then mount /dev/sdd1 somewhere in the filesystem using the mount command or by adding it to /etc/fstab.

---

### Post by jgw on 2023-08-03
Thank you.........

Here is what I have done.  First I checked to see if the bad one was there if I disconnected the good one.  If the good one was there the bad one was there and when not there bother were gone.  

I then took the good one and changed the name from 3tb to test to see what happened.  When I changed the name it was no longer there.  Then I changed the name back to 3tb and, guess what the bad one was now GONE!  I have now rebooted 3 times and the bad one remains gone!  I have also moved it to a new location but will now put it back where it belongs and pray everying thing remains good. 

If it comes back I will give your suggestion a try but, hopefully, the strange one will be gone forever.  

Thank you again for your help!

---

