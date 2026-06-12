---
title: "Problem accessing partitions after PowerQuest. Using TestDis"
date: 2008-02-22
forum: General Help
---

### Post by dpoverlord on 2008-02-22
So here is the run up of the issue.
   I was using my computer fine when I noticed my windows partition had 12 GB left. This partition is on a 400Gb hard drive. C: for windows D: for Data

 I decided to use Powerquest Partition magic to  resize the Windows partition by 10GB and decreasing the data partition by 10GB.

  When my computer rebooted, it would not boot into windows. It would hit the part where it gets close to loading and instead of loading it would reboot.
   I went into the windows Recovery console and did a fixBoot C:
   
Rebooted and did not work.

I did FIXMBR C:\
    And instead it got rid of the partition making it seem like unallocated space.

I then got the Ultimate Boot CD and Knoppix 5.1.0. Before running it I connected another data drive installed windows and used Testdisk. I found the partitions "Wallah" and I found the data  ( WooHoo!). However, I searched deeper and used the write function after analyzing and rebooted. 
   Low and behold, I can not see the whole partition in linux. Then the other drive I installed windows on gives me the error "System error press ctrl alt delete to restart ". 
   No matter what I did nothing ran windows.

So I then Loaded up Knoppix and the ultimate boot cd to get back to testdisk. I run test disk and both drives have the error. "Warning: Incorrect number of heads/cylinder 16 (NTFS) !=255 (HD)".

   I have skipped work trying to fix this issue and I am lost. When I am using testdisk in these environments when I try to push P to view files or rebuild the MBR it exits to a command prompt in the terminal.

    When I use windows to repair the other hard drive off hte cd I still get the system error problem asking me to reboot. When I use TestDisk it shows the partitions but I do not know how to make them available.

   What do you recoomend?

---

### Post by dpoverlord on 2008-02-22
Well,
   I somehow with testdisk got the drives to read. The issue is that I can only get in thru Safe mode and when I run testdisk or partition info from powerquest it says my drive has a geometry issue. 

Testdisk says:
run test disk and both drives have the error. "Warning: Incorrect number of heads/cylinder 16 (NTFS) !=255 (HD)".

I am running Seatools for Dos from Seagate on the drive in advanced mode since nothing was found in basic mode. What can I use  to fix the geometry on the drive?

---

