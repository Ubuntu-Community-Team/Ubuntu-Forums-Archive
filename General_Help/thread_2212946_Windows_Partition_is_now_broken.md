---
title: "Windows Partition is now broken"
date: 2014-03-23
forum: General Help
---

### Post by 3d4tPNm on 2014-03-23
My computer is a **6** year old Windows Vista dual booted with Ubuntu 13.04. (218 gb Windows Vista, 19gb Ubuntu)

I was just setting up some tools until I started to run out of space on my Ubuntu partition, so I decided to repartition my HDD using my Ubuntu boot disk.
The idea was to de-allocate 30 gb from my Windows partition and allocated to my Ubuntu partition. (I had around 30GB of free space left on my windows partition)

Unfortunatly the de-allocation from my Windows Partition failed, which also caused the entire windows partition to become unusable. I am not able to boot into Windows Vista, boot into Windows Vista recovery mode, OR mount the 218 GB volume drive when I am running Ubuntu. Too make things worse, I can't allocate any HD space from that partition either.

This also means I cannot run Chkdsk.


I am for the most part fine with losing Windows Vista, but there are some important things on that partition, such as family photos, and files. Is there anyway for me to recover the data somehow? I have considered using Ubuntu to create a disk image of the windows partition and placing it unto an external drive (so I can at least get some useful HD space for Ubuntu until I can repair Windows), but I assume that would be impossible to do since it is considered broken. 

I do have another windows computer, if plugging it somehow is a solution, but that one is a Windows 7.

Error message when I attempt to mount my Windows partition:

Error mounting /dev/sda1 at /media/jihua/6BC81B24559F13C8: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/jihua/6BC81B24559F13C8"' exited with non-zero exit status 13: Failed to load runlist for $MFT/$DATA.
highest_vcn = 0x6c, last_vcn - 1 = 0x2be3f
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Not really relevant, but the guide I followed for my attempted re-allocation:
[http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/](http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/)

Yes, I am surprised a six year old windows computer is still (barely) running, and yes, it is slower than a snail while running Vista.

---

### Post by scollar1971 on 2014-03-23
Check this out hopefully of some use to you .... I personaly haven't used it though

[http://www.linuxjournal.com/article/9327](http://www.linuxjournal.com/article/9327)

---

### Post by u_i_we_all_buntu on 2014-03-24
Hi I'm sorry to hear about your experience.  

Actually, things aren't necessarily as bad as you think.
It seems that you can still boot Linux, and Linux has apparently detected a problem with the NTFS partition 
and didn't mount the device.

So far so good.  

Now to the business of recovery.  I **strongly suggest** looking at the following site, which mentions various tools that can be used to either recover partitions, or to recover data in damaged partitions:
[INDENT]
**[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")**
[/INDENT]


_My suggestions:_
[LIST=1]
[*] Boot to your Linux partition. Do nothing with the Windows partition.  Leave it unmounted.
[*] Read the recovery guide.  Ignore the parts about failed hardware or device.
- Your Windows partition is on a working device; it just has incorrect partitioning.
- Since you didn't allocate any Windows partition to Linux,  also ignore the part about doing "swapoff". 
[*] Free up about 3gb of disk from your Linux partition.  If possible, backup to USB stick, external drive,etc before deleting
[*]  Even better yet, if you have an external USB hard drive, mount it, so that you can also save recovered files to it.  
[*]  Install the tools that you'll need, as mentioned: **parted** , **testdisk**, **magicrescue**, **photorec**, etc.

Then do:
[*] Attempt partition recovery, as directed, and hopefully, you're done.
[*] If partition recovery fails then use **magicrescue** and/or **photorec** to scour the Windows partition to extract as much data as  possible.
[*] If you have the time and recovery is of the utmost importance, save an image of the windows partition (ie. to an external drive) so that you can recover at your own pace
[/LIST]

Good luck!
  


PS.
I once did something similar, where I trashed the MBR (master boot record) and deleted all partition information. 
Recovery of the partitions was a real pain, because the tools mentioned were not available at the time.

---

### Post by mastablasta on 2014-03-24
it seems "only" partition table is corrupted. You should never resize windows partition with linux tools (well at least not unless the windows side was defragmented and checked). anyway if only the tabel got corrupted the data is still there intact. might be some work to repair it.

checkdisk can run from recovery CD, but in this case if you can not see parittion it might not be enough.

---

### Post by Impavidus on 2014-03-24
Connecting the drive to a working Windows system and attempting file system repair from there may help. In any case make sure your have backups of your Ubuntu files. They should be safe, but you never know.

It's no surprise that Win Vista with just 30GB free disk space on a 219GB disk runs slowly. With 0 free disk space it can stop working completely. I think you need a larger or additional drive. Reallocating small parts of your drive can never buy you more than a few months of time.

By the way, Ubuntu 13.04 is unsupported. Better to move on to 13.10.

---

### Post by Mark Phelps on 2014-03-24
You may be able to repair the partition with a Windows partitioning tool -- Minitool Partition Wizard.  Download the ISO file, burn it to CD, boot from it -- and use the option to recover the partition.  If that works, your partition will be back.

---

### Post by 3d4tPNm on 2014-03-24
Thanks for the responses, i started attempting to use Linux tools; so far I used testdisk and foremost, and neither of which have been successful. 
Testdisk simply says that partition cannot be loaded. While foremost returns "stdin" in terminal, creates the folders for recovery of files, but no files are ever recovered successfully. 

"Connecting to a windows machine", does that entail physically opening up my computer, detaching the HDD and then connecting to a windows machine?

---

### Post by Mark Phelps on 2014-03-24
> 
"Connecting to a windows machine", does that entail physically opening up my computer, detaching the HDD and then connecting to a windows machine? 

Yes, it does ... but you can boot your existing machine from the Minitool Partition Wizard Boot CD and use that directly.  You don't have to remove the drive and connect it to an MS Windows PC.

---

### Post by 3d4tPNm on 2014-03-25
> **Mark Phelps said:**
> Yes, it does ... but you can boot your existing machine from the Minitool Partition Wizard Boot CD and use that directly.  You don't have to remove the drive and connect it to an MS Windows PC.

I just tried out Minitool Partition Wizard Boot CD, it was not capable of repairing or recovering the broken partition.

---

### Post by james114 on 2014-03-25
I think there are some bad sectors on your hard drive,  this thread may help:

[http://ubuntuforums.org/showthread.php?t=2017486](http://ubuntuforums.org/showthread.php?t=2017486)

---

