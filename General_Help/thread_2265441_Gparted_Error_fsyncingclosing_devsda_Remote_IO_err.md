---
title: "Gparted: Error fsyncing/closing /dev/sda: Remote I/O erro"
date: 2015-02-15
forum: General Help
---

### Post by cracktor on 2015-02-15
Hello all

I am having trouble with an external HD. So i installed Gparted to remove older partitions and format it to ext3.
But when i open Gparted it says[B] Error fsyncing/closing /dev/sda: Remote I/O error
[/B]If i click ignore 3 or four times the program starts and i can see my disc.
Partition: unallocated File system: unallocated Size 232,89 GB used- unused- flags
When i try to make a new partition table it gives thesame error.

So what can i do?

---

### Post by oldfred on 2015-02-16
Post these to see if different errors are shown.

sudo fdisk -lu
sudo parted -l

Did drive have partitions?

You may be able to zero out partition table. Make sure you have no data you want to save.
But with dd be extremely careful. I hesitate to use it myself as it also is know as Data Destroyer. Any typo will damage data permanently. 

Make sure you have correct drive. Replace sdX with external drive as show by fstab above.
```
dd if=/dev/zero of=/dev/sdX bs=512 count=1    

    
```

---

### Post by cracktor on 2015-02-16
[COLOR=#000000]Thx for the reply!

Below the outcomes of the commands. The disc i' m talking about is sdb, but since i 'm not too sure what i' m doing  i just post everything. There is no data on disc sdb.
As far as i know the disc did not have any partitions, but i formatted it several times to use it with a tv receiver. So i messed around with it a lot. 
[/COLOR][B][COLOR=#000000]

sudo fdisk -lu[/COLOR][/B]

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x42cc42cc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       204797950   976771071   385986561    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       969439232   976771071     3665920   82  Linux swap / Solaris
/dev/sda6       204797952   969439231   382320640   83  Linux


Partition table entries are not in disk order


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5e1d57e2


   Device Boot      Start         End      Blocks   Id  System



**sudo parted -l**

> Model: ATA TOSHIBA DT01ACA0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  105GB  105GB   primary   ntfs            boot
 2      105GB   500GB  395GB   extended
 6      105GB   496GB  391GB   logical   ext4
 5      496GB   500GB  3754MB  logical   linux-swap(v1)




Warning: Error fsyncing/closing /dev/sdb: Remote I/O error                
Retry/Ignore? r                                                           
Warning: Error fsyncing/closing /dev/sdb: Remote I/O error                
Retry/Ignore? i                                                           
Model: SAMSUNG SP2514N (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags


                               



> 





dd if=/dev/zero of=/dev/sdb bs=512 count=1
dd: failed to open &#8216;/dev/sdb&#8217;: Permission denied









>  sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1


1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0364113 s, 14.1 kB/s



What can i do now?

---

### Post by oldfred on 2015-02-16
After zeroing out partition table does it still give error?

I guess parted should give same error as gparted, same underlying tools.
But fdisk did not see anything?

---

### Post by cracktor on 2015-02-17
> **oldfred said:**
> After zeroing out partition table does it still give error?

I guess parted should give same error as gparted, same underlying tools.
But fdisk did not see anything?

Yes still gave the same error!

---

### Post by oldfred on 2015-02-17
Was drive ever part of RAID, or gpt partitioned? 
Not sure what else might be an issue. Have not seen that particular error.
Does going into Disks and click on icon in upper right corner and then does Smart Data show any issues with drive? It can run many tests, but all I really know is that passed or ok is good, anything else is usually a new drive.

Brute force way might be just to zero entire drive. Would take a long time.

---

### Post by cracktor on 2015-02-17
> **oldfred said:**
> Was drive ever part of RAID, or gpt partitioned? 
Not sure what else might be an issue. Have not seen that particular error.
Does going into Disks and click on icon in upper right corner and then does Smart Data show any issues with drive? It can run many tests, but all I really know is that passed or ok is good, anything else is usually a new drive.

**Brute force way might be just to zero entire drive. Would take a long time.**

I like that, brute force.. how do i do that and how long will it take?
The disc doesnt show up, but i think it was ok in the past.

---

### Post by oldfred on 2015-02-17
There are several drive erase tools. Like dban.

With Ubuntu you can just use dd, but again be absolute sure you have correct drive.
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


 from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)
Zero out drive, larger block size than default is faster
sudo dd if=/dev/zero of=/dev/sda bs=1M

---

### Post by nadarockyraccoon on 2015-02-18
I had this problem with an external drive once, it fell six feet to the hard ground, and died permantly two days later. Try rebooting with the drive plugged in. This worked sparadically, but maybe every third reboot the drive would read fine for a bit, and I managed to get some 60 GB of data before it just stopped registering at all. Powering the drive up and down din't seem to have an effect.I know your goal isn't data retrival, but it may allow you to utilize some other tools to anylyze the disks health or possibly recover it.

---

### Post by cracktor on 2015-02-18
@ oldfred and others: thx a lot for the help. I just think this HDD is dead. So i' m gonna give it a proper burial in the trash can! I recently bought it for 10 euros on dutch ebay, so i' ll just assume there was a problem with it caused by the previous owner..

---

### Post by pseudogeek on 2015-05-06
For others with this message, in my case it turned out to be the enclosure interface (USB-IDE) which was faulty.  The drive itself worked OK in a different enclosure.

I also found that even with the error (faulty interface), I could get Gparted to run a check on the main partition, which would then mount read-only so files could be recovered.

---

