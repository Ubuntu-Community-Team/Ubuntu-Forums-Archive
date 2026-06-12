---
title: "raid drive information lost?"
date: 2008-02-15
forum: General Help
---

### Post by Robbyx on 2008-02-15
3Ware 8006-2 Raid Drive

It was working ok under Fiesty. Under Gutsy gparted reports that it does not contain a valid partition table. THe partition and filesystem is being shown as unallocated. Of course it is not being mounted.

What can I do to access all my data.

Robin

---

### Post by Robbyx on 2008-02-15
I have looked at each drive separately using Gparted by plugging them directly into the sata connections on the MB. Both drives show that the partitions and file systems are uallocated.


 I am very unhappy about the quality of the Gutsy upgrade this problem has caused me enormous problems. 

Is there a way of recovering the data? It was an ntfs drive.

Robin

---

### Post by fjgaude on 2008-02-15
Did you have a driver for the 3Ware when it worked correctly in Feisty? If so, it has to be loaded for Gutsy, perhaps.

BTW, it is normal for raid devices to not show correctly in gparted, for it doesn't yet handle such correctly.

---

### Post by este on 2008-02-15
I have no idea how to fix your issue, but...

I do have experience recovering Raid0 arrays. The easier method I know of is with two windows programs called RaidProbe and GetDataBack by Runtime Software.

I though I lost every thing once but it turns out raid recovery is simple. If it ends up being the only option note that you will need a single drive as large as your array was. I had to do a little hex editing to find some info for the program but I think they cover most raid setups now.


Hopefully you are just having a driver issue.

---

### Post by Robbyx on 2008-02-15
Thank you for your replies. I am surprised that things have gone so wrong. I specifically put all my data on the Raid drive so as to give it added security.


I spoke today to the support at 3ware and we found that Ubuntu Gutsy has the driver included in the distribution. 

I plugged in the hard drives into the sata connections on the board ie bypassed the raid card. Both showed the same ie an unallocated partition.


My raid drives were  set at raid 1


In the mist of all this gloom I have some good news. According to my notes I started this upgrade on 8 Feb. I have been going through my backups and it appears  I did make a backup of all my data on the raid drive just before I upgraded. So things are not so bad, though I am not sure how good is the backup of my thunderbird profile. I have looked in many of the folder on the hard disk backup within the profile and there is nothing in them. I will restore the backup of the thunderbird profile and see what happens.

Any ideas on the recovery of the raid 1 drives would be appreciated in case the backup I made is not good enough.

Another point. 

Any ideas why the upgrade would have wiped out my raid drive contents? I would like to avoid this problem in the future.


Robin


Robin

---

### Post by dean123 on 2008-02-15
> **Robbyx said:**
> Thank you for your replies. I am surprised that things have gone so wrong. I specifically put all my data on the Raid drive so as to give it added security.


I spoke today to the support at 3ware and we found that Ubuntu Gutsy has the driver included in the distribution. 

I plugged in the hard drives into the sata connections on the board ie bypassed the raid card. Both showed the same ie an unallocated partition.


My raid drives were  set at raid 1


In the mist of all this gloom I have some good news. According to my notes I started this upgrade on 8 Feb. I have been going through my backups and it appears  I did make a backup of all my data on the raid drive just before I upgraded. So things are not so bad, though I am not sure how good is the backup of my thunderbird profile. I have looked in many of the folder on the hard disk backup within the profile and there is nothing in them. I will restore the backup of the thunderbird profile and see what happens.

Any ideas on the recovery of the raid 1 drives would be appreciated in case the backup I made is not good enough.

Another point. 

Any ideas why the upgrade would have wiped out my raid drive contents? I would like to avoid this problem in the future.


Robin


Robin


You probably destroyed or damaged the raid info on the drives by connecting them to an onboard raid.

If the controller can't recognize the raid unit, just create a new array and restore your data.

I don't know why the upgrade failed though.  My suspicions is that it altered or corrupt inodes. Good luck.

---

### Post by Robbyx on 2008-02-16
I wish I knew what went wrong.

 I did not connect them to the onboard raid. The bios is set to ide not raid.

The raid drives were ntfs. This means no inodes.

---

