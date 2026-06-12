---
title: "Clone Disk Image to a Network Server"
date: 2015-01-31
forum: General Help
---

### Post by Zythyr on 2015-01-31
The hard drive of my laptop with Windows 8 has bad sectors. The bad sectors is preventing windows from running or being automatically repaired. I backed up all the critical data using Ubuntu live USB. However, some data in my /Users/myusername/Desktop folder didn't get backed up because I am guessing the these files correlate to the bad sectors on the hard drive. 

Before I replace the hard drive and reinstall a fresh copy of windows, is it possible to use Ubuntu live USB to clone the entire hard drive and save the image to a network server? I want to restore the image to a new hard drive to see if the restored image on a new hard drive would allow me to backup the files in the Desktop folder that I was unable to do so. 

The hard drive is 1TB and the Windows partition is around ~900GB. Only 200GB is used in the Windows partition the rest is free space. Would I need to close the entire hard drive or can I get away with only cloning the windows partition? 

How would I go about cloning the image and restoring it using Ubuntu Live USB? Is gparted the right software to do so? If so how do I do it?

---

### Post by sandyd on 2015-01-31
> **Zythyr said:**
> The hard drive of my laptop with Windows 8 has bad sectors. The bad sectors is preventing windows from running or being automatically repaired. I backed up all the critical data using Ubuntu live USB. However, some data in my /Users/myusername/Desktop folder didn't get backed up because I am guessing the these files correlate to the bad sectors on the hard drive. 

Before I replace the hard drive and reinstall a fresh copy of windows, is it possible to use Ubuntu live USB to clone the entire hard drive and save the image to a network server? I want to restore the image to a new hard drive to see if the restored image on a new hard drive would allow me to backup the files in the Desktop folder that I was unable to do so. 

The hard drive is 1TB and the Windows partition is around ~900GB. Only 200GB is used in the Windows partition the rest is free space. Would I need to close the entire hard drive or can I get away with only cloning the windows partition? 

How would I go about cloning the image and restoring it using Ubuntu Live USB? Is gparted the right software to do so? If so how do I do it?

You can clone the disk to another disk or to an image. I suggest gddrescue due to bad sectors.

See [https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive) for instructions on how to use.

---

### Post by Zythyr on 2015-02-01
So I ran the dd command to clone the bad hard disk to a larger hard drive. The dd command gave me input/output error, so I ran the dd command again using the option conv=noerror,sync. Since the corrupted drive is 1TB, its it taking almost 24hour to finish. 

I just found out about the gddrescue. Does this mean I will have to restart the entire process and let ddrescue clone (and fix) the corrupted drive to the new hard drive? 

In Ubuntu, I am able to mount the Windows partition (C drive) of the courrupted hard drive. Only few files within the Desktop folder (which i need to backup) are corrupted. Can't I ddrescue (and fix) only the files located in the Desktop folder to save time??

---

