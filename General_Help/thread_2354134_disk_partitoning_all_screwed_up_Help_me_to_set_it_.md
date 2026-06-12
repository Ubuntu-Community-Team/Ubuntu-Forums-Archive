---
title: "disk partitoning all screwed up Help me to set it back to completely empty device"
date: 2017-02-28
forum: General Help
---

### Post by neill-rutherford on 2017-02-28
Hello
In copying a backup of a 80 GB hard drive I got an I/O error 

Disks reports SAMSUNG HM250HI (01C4) 250 GB (250,059,350,016 bytes)

sudo fdisk -l Only reports the internal disk sda partitions

sudo blklid
/dev/sda1: LABEL="Boot" UUID="d4bf4ff0-a4d4-4cb3-853c-75bfc5659b99" TYPE="ext4" PARTUUID="e654426c-af0b-4a2b-89f2-cb162ba92557"

...

/dev/sda13: LABEL="HDD" UUID="30740BC1740B88B4" TYPE="ntfs" PARTUUID="10a838a6-4adf-40f6-add2-e2477a4f5d68"
**/dev/sdb1: UUID="954a6ec9-877b-4582-baa2-8293764903c5" TYPE="ext4"**

Disks show partition 1 8.6GB  unknown ext4 partition 2  = 71GB unknown unknown free space 170GB

Gparted shows a 1.86GB filling whole disk.

[SIZE=5][B]How do I get back to a MSDOS partitioned disk of 250 GB unallocated ?
[/B][/SIZE]

---

### Post by ajgreeny on 2017-02-28
Do you need any of the files on that disk?

If it is possible to work on it with no worries about current contents just go to Device in gparted and choose to create a new partition table, assuming that is an option open to you.  Once you have the partition table you can then create new partitions in the unallocated space.

Just make sure the disk/partitions are all unmounted before you try any of this or you will not be able to do anything.

---

### Post by neill-rutherford on 2017-02-28
No there is nothing i want on sdb 250GB disk but gparted now only shows it as 1.86GB. How do I get the 250gb back?

thank you for helping

how it started was I was cloning an 80 GB drive to transfer to a 250 gb drive Samsung HM250HI LBA 488 397 168 250GB and I got an error
and now I can't get back to a blank 250GB drive or at least ii don't know how to

Neill


[INDENT]   neill@neill-HP-G61:~$ sudo dd if=/dev/sdb of=jimbackup.raw bs=32256
2480976+0 records in
2480976+0 records out
80026361856 bytes (80 GB, 75 GiB) copied, 2617.58 s, 30.6 MB/s
neill@neill-HP-G61:~$ ^C
neill@neill-HP-G61:~$ sudo dd if=jimbackup.raw of=/dev/sdb bs=32256
[sudo] password for neill: 
    **dd: error writing '/dev/sdb': Input/output error**
50607+0 records in
50606+0 records out
1632378880 bytes (1.6 GB, 1.5 GiB) copied, 199.994 s, 8.2 MB/s
neill@neill-HP-G61:~$
  
 [/INDENT]

---

### Post by neill-rutherford on 2017-02-28
i move the disk from a USB 2.0 to sata/ide combo adapter into the internal disk slot on another laptop and I was able using Disks program to delete the offending partitions and get the drive back to being 250GB. I am now using  dd if=x of=/dev/sda conv=noerror bs=64 hoping this time it will copy the backup of the source disk.

---

