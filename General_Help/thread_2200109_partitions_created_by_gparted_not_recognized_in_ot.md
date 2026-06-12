---
title: "partitions created by gparted not recognized in other OS (Windows)"
date: 2014-01-17
forum: General Help
---

### Post by two4two on 2014-01-17
I have three HDDs.   I used gparted to create partition tables and partitions.  I had problems on one of the drives (similar to what I'm describing in this thread), but I've overcome ththose problems.  Here's the layout:

sda = 500G IDE drive 
sda1 = 80G NTFS primary partition with Windows XP working (this is the problem I have solved)
sda2 = 80G ext4  primary partition for future Linux distro
sda3 = 80G NTFS primary partition for possible future OS
sda4 = 260G extended partition
sda5 = 130G NTFS partition for data
sda6 = 150G NTFS partition for data
sda7 = 5G linux swap partition


sdb = 500G IDE drive 
sdb1 = 80G NTFS primary partition with Win 7 used to work, but since I re-installed WinXP on sda1 the boot loader is gone
sdb2 = 80G ext4  primary partition has Ubuntu Studio 11.04 (Natty) works OK
sdb3 = 80G ext4  primary partition for possible future OS
sdb4 = 260G extended partition
sdb5 = 130G NTFS partition for data
sdb6 = 150G NTFS partition for data
sdb7 = 5G linux swap partition

So far so good.  Ubuntu recognizes and has data on all partitions and WindowsXP recognizes and has data on all NTFS partitions.

So I added a 3T SATA drive.  I originally attempted to use gparted to create the following:

sdc = 3T SATA drive 
sdc1 = 80G NTFS primary partition for future install of Win8.1
sdc2 = 80G ext4  primary partition for future OS
sdc3 = 80G NTFS primary partition for future OS
sdc4 = 2,850G extended partition   [COLOR="#FF0000"][/COLOR]**FAIL!!!!!!! too big for MBR-style partition table architecture.**
.
.
.

So I instead created

sdc = 3T SATA drive 
sdc1 = 80G  NTFS primary partition for future install of Win8.1
sdc2 = 500G NTFS  primary partition for future OS
sdc3 = 1.6T  ext4   primary partition for data
sdc4 = 780G NTFS primary partition for data

But WindowsXP only saw the 4th partition (sdc4) -- 780G NTFS.  It couldn't see the 1st (80G NTFS) or 2nd (500g NTFS), and I would expect it to see the 3rd (sdc3 etx4).



So I used gparted once again to overhaul the drive to look like:

sdc = 3T SATA drive 
sdc1 = 80G NTFS primary partition for future install of Win8.1
sdc2 = 80G ext4  primary partition for future OS
sdc3 = 1.3T NTFS primary partition for data
sdc4 = 1,495G extended partition
sdc5 = 1,490G ext4 partition for data
sdc6 = 5G linux swap partition

And guess what?  WinXP STILL thinks there's only a 780G NTFS partition and nothing else!

What am I doing wrong?????


Thanks in advance for bearing with my exceeding inexperience.

---

### Post by Bucky Ball on 2014-01-17
Have you tried setting it up with Windows tools and adding the EXT4 partition with Gparted in Linux?

Windows will not see the EXT4 partition, or any EXT* partition, at least not as an EXT partition. It might call it something like 'Healthy' in Disk Management and that's about it.

---

### Post by Bucky Ball on 2014-01-17
Have you tried setting it up with Windows tools and adding the EXT4 partition with Gparted in Linux?

Windows will not see the EXT4 partition, or any EXT* partition, at least not as an EXT partition. It might call it something like 'Healthy' in Disk Management and that's about it.

Just a side note: You appear to have a lot of primary partitions. Ever used extended partitions? They act like a holder for logical drives/virtual partitions which act exactly the same way as any other partition. The advantage is you can have as many logical drives inside and extended partition as your hardware can handle. You are not limited to four partition per physical drive.

Windows is best on partition one, drive one, and always a primary partition, but Ubuntu will happily exist on a logical drive inside an extended one.

---

### Post by oldfred on 2014-01-17
XP does not have drivers to work with gpt partitioned drives. 
And MBR which was designed over 30 years ago has a max of 2.2TiB.

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

        GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by two4two on 2014-01-17
> **Bucky Ball said:**
> Have you tried setting it up with Windows tools and adding the EXT4 partition with Gparted in Linux?

Windows will not see the EXT4 partition, or any EXT* partition, at least not as an EXT partition. It might call it something like 'Healthy' in Disk Management and that's about it.

Just a side note: You appear to have a lot of primary partitions. Ever used extended partitions? They act like a holder for logical drives/virtual partitions which act exactly the same way as any other partition. The advantage is you can have as many logical drives inside and extended partition as your hardware can handle. You are not limited to four partition per physical drive.

Windows is best on partition one, drive one, and always a primary partition, but Ubuntu will happily exist on a logical drive inside an extended one.


I knew Windows could not recognize ext4 partitions.  Funny how Linux can do everything Windows, but Windows can do nothing Linux.

I am using MBR partition structure which says I can have 4 partitions.  In order to use extended partition you need to give up one of the primary partitions -- which I generally do.  I use primary partitions in order to be able to have flexibility as to which OS I can install.  I understand what you said about Linux being OK anywhere but Windows is not.  Thus my Windows installations go in primary partition 1.

But my problem is simply that Windows XP is having problems with my 3TB drive.  It can't recognize the partitions as I have set them up using gparted.

But I think I have stumbled onto an something.  It stems from a deficiency in the MBR partitioning structure.  It is a 32-bit architecture and thus can't address beyond 2TB.  According to Windows XP it is an invalid partition structure.  It doesn't explain why it DOES recognize a 780G partition that lives so far into the disk and why it doesn't recognize an 80G partition in the very beginning of the disk.  It also doesn't explain why LINUX has no problem whatsoever with the MBR structure on this 3TB drive.

I've read that there is a workaround for Windows and I'm pursuing it.  

I've also read about more modern partitioning architectures such as GPT.  But I don't know which version of Windows (WinXP, Win7, Win8), IF ANY can use it.  And I certainly don't know how to set it up or if gparted can set it up.

So, that's my status update.

Anyone?

---

### Post by slooksterpsv on 2014-01-17
Gpt can be setup in vista on up iirc. I've used 7in gpt and mostComputers post 7 use gpt for uefi purposes. Have you went into disk management and told it to mount the NTFS volumes?

EDIT: Gah can't type on a Nexus 7, let's try that again:
Yes Vista supports GPT and XP 64-bit does for DATA ONLY

With the ntfs partitions created, try to mount them using the disk management utility in Windows (diskmgmt.msc); sometimes Windows won't automatically mount it. You may need to run a check disk as the bitmap file may be corrupt with partitioning in Linux (happens often as Windows is very specific of how to create partitions).

Otherwise upgrade to 7, 8, 8.1 or just stop using XP and switch to Linux.

---

### Post by two4two on 2014-01-17
> **oldfred said:**
> XP does not have drivers to work with gpt partitioned drives. 
And MBR which was designed over 30 years ago has a max of 2.2TiB.

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

        GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Thank you oldfred.  I will read these links and mark this thread appropriately afterwards or start new thread.

---

### Post by two4two on 2014-01-17
I read on Microsoft.com that WinXP Home will be OK with GPT disk, but it doesn't say whether or not it has to 64-bit.  I checked on gparted docs and it should straight-forward to set up the gpt disk.  So WTH, I'll give it a try and report back.

---

### Post by oldfred on 2014-01-17
Someone just posted this link to Microsoft's gpt info. XP has to be 64  bit to read gpt partitions.
[http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx)

I dual booted since 10.10 with a gpt partitioned small drive and XP on MBR drive. I just kept any data I needed for XP on MBR drive.

---

### Post by two4two on 2014-01-24
Marking this as solved.  Win XP 32-bit will never see this disk.  Also, any win-64-bit could only SEE the partitions; never boot from them.

My Win7 and Win8 64-bit have no problem seeing them and working with them.  My WinXP 32-bit can not see them and never will.  

So, this thread is solved.


BTW!!!!!  Ubuntu has NO PROBLEM at all with this disk!!!  Ubuntu rules.

---

