---
title: "Re-using RAID disks"
date: 2008-02-05
forum: General Help
---

### Post by joven on 2008-02-05
On a computer, which I no longer have access to, I setup a RAID 5 array in Software on Ubuntu 6.06 lts. (I can't remember if the RAID array was bootable and had the OS on it though)

I have 2 of the 3 drives (Seagate 750gb sata), and I need them for another computer, which is running Windows.  But I cannot seem to get them to work properly in anything.

Windows will show them in Disk Management, but all options are greyed out, as I wasn't really expecting windows to do anything with them, I didn't think too much of it, but when I boot to my GPartED liveCD it wont get past making a disk label (makes me do it every time I try to make a new partition.)

I tried the Seagate DiskWizard bootable hard drive utility, told it to make an ntfs partition on the drive.  I tried making a 1 gig partition on one, thinking if nothing else then windows would be able to use that 1gb and i could just do the same thing on the whole drive.
But, after it goes through making that 1gb partition (took about 45 minutes), Windows still cant do anything with it, I plug it in to my Mac, and DiskUtility says its unformatted, and cant partition it.
I'll see if I can do anything with the other drive which is making a partition on the whole drive overnight (gonna take well over 8 hours), but at this point Im not really hopeful.

I tried just installing Ubuntu on it with the alternate installer CD, stops at 33% on the partitioning, and again the drive is unusable.

Does software RAID with Linux irreparably damage the drives used? 
How can I use these drives again for anything?  
The only thing I see about software raid is about how to set it up, I cant seem to find anything about ever using those drives again for anything else.

---

### Post by tad1073 on 2008-02-05
I had the same experience with the raid 5 i had. My solution was to disable the raid arrray which wiped out w2k-no big deal on tnat though- I installed ubutnu on the first drive and used the other two as storage. I even tried a raid 0 but no beans on that either. My drives are only 9gb each so i gained about 9gb of space. ubuntu does not like raid arrays!!!

My advice would be to diable the raid, if that is what you want to do. Then make the other two drive mountable etc. etc.

---

### Post by joven on 2008-02-05
My problem isn't with getting an array setup or anything like that (they **were** in an array, which worked fine) and I cant just disable it, the system they were part of is no more.

My issue is that now that that system is no more (it didn't fail or anything, it was forcefully repurposed), these drives are practically worthless because no matter what I try, I cant put them in another computer and have them work.

---

### Post by tad1073 on 2008-02-05
So your saying that the motherboard that those drives were attached too are gone? you do not have the case or any of the other components?

---

### Post by joven on 2008-02-05
Right.
And I want to take those drives, and use them on another computer, which is running Windows.

---

### Post by fjgaude on 2008-02-06
I'm not sure what is going on but it sounds like you don't have a disk label on the old raid drives.

If you can go into gparted with the drives attached to the OS, Ubuntu is fine, and click on one of them. From there click on the menu Device, Set Disklabel and then Advanced. Use msdos and then Create. That should clear the raid headers and the disk should work in terms of being formatted, etc.

---

### Post by joven on 2008-02-06
Ive done that, several times.  On a gparted liveCD, and on Ubuntu, and QTpartED in Kubuntu.
It never takes.  I create the disklabel, go to make a new partition, it says I need to make a disk label, rinse, repeat.

---

### Post by fjgaude on 2008-02-06
Amazing...  never ran into such a situation before... I've reused raid disks many times. Will put the thinking cap on. <smile>

---

