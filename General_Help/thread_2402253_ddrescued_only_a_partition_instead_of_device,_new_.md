---
title: "ddrescued only a partition instead of device, new drive wont boot"
date: 2018-09-27
forum: General Help
---

### Post by squiigee on 2018-09-27
I already lost this post to the whims of Chrome page reloading, so this retyping might be a little more terse :(


I had a failing 500GB HDD on a Thinkpad X240, with Ubuntu installed. The imminent failure was indicated by fallbacks to busybox shell on boot, requests to run fsck, and switching to readonly mode after some time period when I did manage to get it to boot to the Ubuntu desktop. 


 The drive [OldDrive] had an msdos partition table, and 2 partitions (Ubuntu install on /dev/sda1, linuxswap on /dev/sda2), and then a bunch of unallocated space.


I bought a new 1TB HDD [NewDrive]. I thought, to reduce time and/or wear, that I would only (need to) copy the partition from OldDrive with the OS install, /dev/sda1, which was only 180gb.


//probable start of user-errors


With a liveusb I partitioned NewDrive, initializing with a GPT partition table (as Googling gpt vs msdos showed gpt to be the recommended consensus). 
I then created 3 partitions /dev/sdb{1,2,3}. /dev/sdb1 to host the transplanted install, /dev/sdb2 as swap, and /dev/sdb3 as a data partition (and initial destination of the file to be imaged from /dev/sda1).


So I ran:


sudo ddrescue -f -n  if=/dev/sda1 of=/media/ubuntu/NewDrivePartition3/ddrescued_partition.img


I then dd'd that ddrescued_partition.img to /dev/sdb1, and patted myself on the back, thinking I was done.


But the machine can't boot. I try boot-repair from a liveusb and it doesnt work, complaining that: 


"The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition(FAT32, 100MB~250MB, start of the disk,boot flag)."


I was kinda lost at this point, and some other thread (lost it now) claimed that boot-repair works better with msdos rather than GPT, so I use fdisk to convert the start of NewDrive to msdos from gpt, but boot-repair still didnt work. 


Thankfully rEFInd on a liveusb can see the install and boot into the Ubuntu install on NewDrive, but thats not sustainable.


How do I fix this "a little information is a dangerous thing" hole I've dug myself into? Do I actually need to create a new 250MB EFI partition at the start of the disk, and wait N hours for everything else to shift 250megs to the right?


I didnt consider any separate boot partition initially because this 250meg EFI partition isn't present on the original OldDrive. I've never consciously noticed anything like it before, though another X220 I just checked does have this /boot partition. Both Thinkpads are running 16.04, so I'm not sure why one has it and the other doesn't.


tl;dr: ddrescued only a partition instead of device, now new drive wont boot because of EFI/grub/partition table/something else. What to do?

---

### Post by HermanAB on 2018-09-28
So, you have one corrupted old drive and a brand new drive.

Install Linux on the new drive, so that you have a working machine, then try to save your data from the old drive.

Don't bother with the system files on the old drive - just save your data.

---

### Post by yancek on 2018-09-28
From the info you posted, your old Ubuntu install was a Legacy/MBR install so that simply copying the old system partition to a new partition will not make it bootable as there is no boot code in the MBR pointing to the partition to which you copied Ubuntu on the new drive.

Doing a new install as suggested above would seem to be the simplest solution.

---

### Post by squiigee on 2018-09-28
Thanks for the response. The desire to keep the system files is because its a dev machine...I've probably got a bunch of self-downloaded headers in /usr/include or self-built binaries in /usr/local/bin that I can't immediately remember...so that'll be extra work in the future.

Being able to directly go from physically failing drive to drive image to bare metal install on new drive would be awesome, rather than reinstall OS, reinstall user programs, restore user data, restore custom built stuff in /usr/* ....

---

### Post by TheFu on 2018-09-28
for complex boot issues like this, begin by providing full information.  boot-repair will gather that and provide a URL.  Post that here. Then someone can use those facts to tell you the shortest answer.

But really having backups that are fresh and consistent enough to be restored is the best answer.  There are many different methods for generating those. Each of us posting here have different methods.  Mine is probably more complex than most,  but I can have a restored system in 30-45 minutes.  Desktops are faster.  Servers take a little longer mainly do to the TB of data that needs restoring.  Regardless, the server is up and working in 30-45 min, just all the data is missing and being restored from that point on.  

BTW, if you need /usr/local/ anything, include that in your backups.  I do.

---

### Post by yancek on 2018-09-28
Why not use clonezilla to image the old drive?

---

### Post by squiigee on 2018-09-28
I was under the impression that ddrescue is the (non-professional) gold-standard for drives that are tottering on their last legs. Also, if there did turn out to be a lot of errors on the filesystem (I'm not sure if clonezilla gives you that information, as ddrescue does), I wouldnt writeback the image file to bare metal - I'd just mount the image and pull the files off. From what I understand, you can't mount clonezilla image files.

That said, I'll be using clonezilla for future backups, or carbon copy cloner, I need to compare them more thoroughly...

---

### Post by TheFu on 2018-09-28
**ddrescue** tries to get every byte off the failing storage that it can.  Multiple times.  This is good for data recovery, if backups aren't available. For failing storage, I think ddrescue is the only option short of professional data recovery hardware.

If the entire device was cloned using ddrescue directly onto the new storage, then the system probably wouldn't have had any issues, beyond those unknown parts that have been corrupted by the original storage.  This assumes the sector sizes for both storage devices are the same.  If they aren't, say one is 512b sectors and the other is 4Kb sectors, it is probable that the partitions would be misaligned, which will cause about a 30% performance decrease. 

However, image-based backups have numerous issues. Primarily the time required for imaging since every byte gets copied.  Restoring to smaller storage isn't allowed with image-based solutions. The other problem is the storage required to have 60-90 days of backups.   **fsarchiver** solves some of the issues, but not all.  Most of the new image-based solutions compress the image and some understand file systems, but they still need a quiesced partition to ensure the image isn't corrupted by open files.

For regular, daily, automatic, backups, there are many better solutions.  Many. None of these are image-based.

IMHO.

---

