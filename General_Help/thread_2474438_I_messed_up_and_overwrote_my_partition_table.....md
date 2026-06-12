---
title: "I messed up and overwrote my partition table...."
date: 2022-04-29
forum: General Help
---

### Post by fmanu on 2022-04-29
So i did something stupid :-(


I was trying to add a new partition but in doing so my partition table was overwritten.
The system is still running but i'm sure a reboot is not a good idea at the moment.


I found this info:[https://surfer.nmr.mgh.harvard.edu/partition/partition-6.html](https://surfer.nmr.mgh.harvard.edu/partition/partition-6.html)
but i don't know the exact number of sectors for the existing partitions.
The article suggests to "Make a partition that is at least as big as your first partition was".  But making one partition bigger will make the other one too small, so it has to be exactly right.

This is the information i have at the moment :
lsblk:
NAME                   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
vda                    252:0    0  300G  0 disk 
&#9500;&#9472;vda1                 252:1    0  150G  0 part 
&#9474; &#9500;&#9472;ubuntu--vg-root   253:0    0  249G  0 lvm  /
&#9474; &#9492;&#9472;ubuntu--vg-swap_1 253:1    0  980M  0 lvm  [SWAP]
&#9492;&#9472;vda2                 252:2    0  100G  0 part 
  &#9492;&#9472;ubuntu--vg-root   253:0    0  249G  0 lvm  /




I also printed the partion-table before making any changes:
parted -l
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1028MB  1028MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 267GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  267GB  267GB  ext4




Model: Virtio Block Device (virtblk)
Disk /dev/vda: 322GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  161GB  161GB  primary               boot, lvm
 2      161GB   268GB  107GB  primary               lvm
----------------------------------------------------------

With this info can someone help me restore the partion table?
This is on a VPS running Ubuntu 18.04.

---

### Post by dragonfly41 on 2022-04-29
You are correct. Keep your OS running to repair.
Install **testdisk** from repo and hunt around for discussions on how to use it to recover partition.

Here is one I just found.

[https://www.simplified.guide/linux/disk-recover-partition-table](https://www.simplified.guide/linux/disk-recover-partition-table)

[P.S.] Since you have Ubuntu already running you can start from Step 6
in above guide.

---

### Post by TheFu on 2022-04-29
This probably won't be much use.  Get your backups ready.

This is the table you have to reproduce.  All the LVM stuff in the list above is inside it.
```
Model: Virtio Block Device (virtblk)
Disk /dev/vda: 322GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number Start End Size Type File system Flags
1 1049kB 161GB 161GB primary boot, lvm
2 161GB 268GB 107GB primary lvm
```
Not much to go on.  Did you dd over the first table or both copies?  msdos puts both copies, a primary and a backup, together.  GPT would put the primary copy at the start of the space and the backup at the opposite end.  You've heard that GPT partition tables have lots of great things?  This is one of them.
I've never seen an Ubuntu partition that is marked as both LVM and boot. Interesting. I don't know what to make from that. Sorry.

Too bad your print isn't the output from **sudo parted -lm**.  That would provide an exact copy in a format that could be fed back into parted and recreated.  For example, here is the vda/vdb for my main desktop:
```
BYT;
/dev/vdb:10.7GB:virtblk:512:512:[COLOR="#008000"]gpt[/COLOR]:Virtio Block Device:;
1:1049kB:10.7GB:10.7GB:::lvm;

BYT;
/dev/vda:32.2GB:virtblk:512:512:[COLOR="#FF0000"]msdos[/COLOR]:Virtio Block Device:;
1:1049kB:538MB:537MB:fat32::boot;
2:539MB:32.2GB:31.7GB:::;
5:539MB:32.2GB:31.7GB:::lvm;
```
It is a VM and uses LVM too.  The partition table alone isn't enough to fix this problem.  The mount locations and file systems are necessary too.  I include this information in my backups, along with lvs, vgs, pvs information, after seeing that many people (not me, at least not yet), do corrupt their partition tables.  I've always assumed that someday I'd do it too.  Preventative data gathering. Takes less than 1 second in the backup script.

You'll also see above that vda is msdos ... a mistake by the installer.  I go out of my way now to use gpt partitions. Didn't always do that.  You can try to dump the partition table that is in memory, then force that back onto disk.  Assuming it is still in memory. I have doubts that will be possible.

There are other ways to get a machine-readable partition table for backups, btw.

Also, please, please, post using forum code tags any terminal commands+output so we can see it as it was meant, in the correct columns.  lsblk output without proper layout will often cause bad answers.

As a precaution, I hope you've already backed up all the settings (system and personal), plus all the data and a list of installed packages, since this could easily go bad.

---

### Post by oldfred on 2022-04-29
I do not know if sfdisk is reading partition table or using mounted partitions.
Does this show partitions or not?
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors and save:
sudo parted /dev/sda unit s print

---

