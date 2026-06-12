---
title: "Need a bit of assistance - Moving an encrypted LVM to the end of the disk"
date: 2018-07-14
forum: General Help
---

### Post by carlo-1973 on 2018-07-14
Hi there everyone.
I am not a new user to Linux or Ubuntu, but I have never tried (or needed to) enlarge an encrypted LVM partition before.
I realize I have to move the LVM partition to the end of the disk before it can be enlarged.
I followed this guide: [URL="https://matthiaslee.com/moving-a-luks-encrypted-lvm-with-dd-and-sfdisk/"]https://matthiaslee.com/moving-a-luks-encrypted-lvm-with-dd-and-sfdisk/
[/URL]Everything went fine until the end where I am committing the new partition table.
Bellow you will see the command output and subsequent error
You will notice that there is no /dev/sda3 - but this seems to be where the script is bottoming out.
At the bottom is the contents of the partition.dump file being used to import.

additional information:  original disk was 400 GB and the new one is 650 GB.
Original LVM partition was 250GB.

Once I have this moved over I should be able to properly extend it using another guide I found on this forum previously.


Edit: managed to figure out how to fix the initial failure regarding the non-existant /dev/sda3 drive.
New error: get's to /dev/sda5 and fails with an invalid argument.
Updated the output and the dump file information here.
Also added how I got my calculations for the new start value for /dev/sda5 at the end.

Output from command
> Disk identifier: 0xe77d55de

Old situation:

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1456127   1454080   710M 83 Linux
/dev/sda2       1501182 524285951 522784770 249.3G  5 Extended
/dev/sda5       1501184 524285951 522784768 249.3G 83 Linux

>>> Script header accepted.
>>> Script header accepted.
>>> Script header accepted.
>>> Script header accepted.
>>> Created a new DOS disklabel with disk identifier 0xe77d55de.
/dev/sda1: Created a new partition 1 of type 'Linux' and of size 710 MiB.
Partition #1 contains a ext4 signature.
/dev/sda2: Created a new partition 2 of type 'Extended' and of size 249.3 GiB.
/dev/sda3: Ignoring partition.
/dev/sda4: Ignoring partition.
** /dev/sda5: Failed to add #5 partition: Invalid argument**
Leaving.


partition.dump file
>   GNU nano 2.9.3                                   partition.dump                                             

label: dos
label-id: 0xe77d55de
device: /dev/sda
unit: sectors

/dev/sda1 : start=        2048, size=     1454080, type=83, bootable
/dev/sda2 : start=     1501182, size=   522784770, type=5
/dev/sda3 : start=           0, size=           0, type=0
/dev/sda4 : start=           0, size=           0, type=0
** /dev/sda5 : start=   840364032, size=   522784768, type=83**



new partition start calculations
> device: /dev/sda
unit: sectors

/dev/sda1 : start=        2048, size=     1454080, type=83, bootable
/dev/sda2 : start=     1501182, size=   522784770, type=5
/dev/sda5 : start=     1501184, size=   522784768, type=83



lubuntu@lubuntu:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 650 GiB, 697932185600 bytes, 1363148800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe77d55de

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1456127   1454080   710M 83 Linux
/dev/sda2       1501182 524285951 522784770 249.3G  5 Extended
/dev/sda5       1501184 524285951 522784768 249.3G 83 Linux
lubuntu@lubuntu:~$ 


**  total sectors - partition size = new start**
partition size=   522784768
1363148800 sectors
** new start: 840364032**



---

### Post by oldfred on 2018-07-15
I do not know LVM.

I often find it easier just to do a new install to a new drive and then copy data over. Mostly /home, and often some settings in /etc. If a server you may other folders with database or web data you also need to copy.

You do not have an sda3. With MBR partitioning the primary partitions are all 1 thru 4. And any one of the primary can then be an extended partition with any number of logical partitions starting at sda5. You have one logical partition which is your LVM with whatever volumes you have in it.

I believe you just have to extend the physical partition by first enlarging the extended partition and then its logical partition. Then you have to use LVM tools to expand LVM inside the physical partition.
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by HermanAB on 2018-07-16
Err... Playing with partitions and moving encrypted data is almost a guaranteed way to lose everything.

So, first make a backup, then experiment.

---

