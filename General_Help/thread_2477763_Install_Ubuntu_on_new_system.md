---
title: "Install Ubuntu on new system"
date: 2022-08-06
forum: General Help
---

### Post by daanheuvelbeuk on 2022-08-06
Next week I will be receiving my new system. I want to transfer my Ubuntu HD to it. Is that just connecting the HD using SATA, plugging in the flash drive with the newly downloaded Ubuntu install and boot?

---

### Post by ajgreeny on 2022-08-06
Impossible to answer that without a lot more info about both the old and new hardware but suffice to say that you will not have the same difficulties as you would transferring a Windows hard disk which will be limited to the hardware on which it is running.

If all your old hardware, ie disks, etc, will connect to the new hardware there is a good chance that it will work though you may have to run a live system and edit some system files such as /etc/fstab.

Try it out and report back any problems.

---

### Post by arraybolt3 on 2022-08-07
If you're reinstalling Ubuntu from scratch, and your new system supports SATA, and Ubuntu can recognize all of the hardware and work with it in a way that functions properly, then yes, this should work just fine. It sounds like you're installing Ubuntu from scratch if you're using a flash drive with Ubuntu on it, and Ubuntu generally does a very good job of recognizing hardware, so I'm willing to say this has a good chance of working. The one real trip-up you might run into is Intel Rapid Storage Technology (RST), which you can fix by going into the BIOS and changing your hard drive mode from RAID to AHCI in the event that happens.

---

### Post by ajgreeny on 2022-08-08
I missed your comment about the USB drive, so are you installing/attaching a disk that already has Ubuntu OS on it or reinstalling the OS from that USB on to a disk?

---

### Post by daanheuvelbeuk on 2022-08-09
What I want to accomplish is move the data from the old system to the new system. So  I probably have to reinstall, as  the hardware is completely different from the old system. So the old OS will probably not work.

---

### Post by tea for one on 2022-08-09
> **daanheuvelbeuk said:**
> What I want to accomplish is move the data from the old system to the new system. 
Have you backed up your data?
If so, then quite easy to move to a new system.

---

### Post by oldfred on 2022-08-09
I have an external SSD with my data.
It gets mounted automatically at /media/fred/data256 as I labeled data partition as data256.
I then have multiple folders in that data partition and created a script with multiple lines like this to copy each folder.

rsync -aruvP /media/fred/data256/Documents /mnt/data

The destination is my data partition (not /home). But you can use rsync to copy from your old drive to your new system.

---

### Post by TheFu on 2022-08-10
> **daanheuvelbeuk said:**
> What I want to accomplish is move the data from the old system to the new system. So  I probably have to reinstall, as  the hardware is completely different from the old system. So the old OS will probably not work.

That may not be necessary, but "it depends" is the only viable answer.
I've moved HDDs between systems multiple times and it has worked.  The only real issues were to remember to remove any proprietary GPU drivers if the new system doesn't use the same GPU.   And if the old system is running a hypervisor, then you may need to change the default CPU model for VMs to match the new CPU model. This would be manual changes.

Really new hardware can cause issues.  If the new has been available less than 1 yr, I'd expect some drivers won't be available in the old OS and perhaps not in 22.04.1 either. Just depends on how new everything is.


So ... "it depends" is the answer.  Plan for the worst, but hope for the best.

---

