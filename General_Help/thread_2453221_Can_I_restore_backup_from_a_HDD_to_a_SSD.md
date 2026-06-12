---
title: "Can I restore backup from a HDD to a SSD?"
date: 2020-11-05
forum: General Help
---

### Post by pretty_whistle on 2020-11-05
I made a backup of a HDD and now I'd like to restore the backup to a SSD.  I used Clonezilla.  Can I do this?

---

### Post by tea for one on 2020-11-05
You haven't been very specific about the type of backup.

Is this a full system OS backup including home directories and multiple users?
Is it just a data backup?
Is it multiple operating systems?
Is it a Windows backup?
Partition backup or disk backup?

Generally, yes, you can restore HDD data to SSD (providing your destination is larger than your source)

However, please add some details.

---

### Post by GhX6GZMB on 2020-11-05
I'm not sure that Clonezilla is the right tool for this. I'd tend more towards a file-based backup system.
This of course presumes that you've prepared the SSD with a fresh installation first, but I'd always do that when changing system disks.

---

### Post by pretty_whistle on 2020-11-05
> **tea for one said:**
> You haven't been very specific about the type of backup.

Is this a full system OS backup including home directories and multiple users?
Is it just a data backup?
Is it multiple operating systems?
Is it a Windows backup?
Partition backup or disk backup?

Generally, yes, you can restore HDD data to SSD (providing your destination is larger than your source)

However, please add some details.

To answer your questions:

It's a full system OS backup.
Just Ubuntu.
It's a disk backup.

You said providing your destination is larger than your source.  It's a disk backup of a 1T HDD.  The SSD is only 512 GB in size.  Isn't an OS backup just a backup of the OS itself and not the free space on the drive?

---

### Post by tea for one on 2020-11-05
Unfortunately, Clonezilla will not allow you to restore to a smaller destination with a complete disk backup.
Clonezilla does not ignore free space.

Here is a suggestion:-

Use gparted in a [COLOR="#0000FF"]live[/COLOR] Ubuntu session to reduce your partitions so that they are smaller than your destination.

Create the exact size partitions on your destination disk.

Use Clonezilla to create an image using partitions.

Then restore to your smaller SSD.

By the way, do not try to reboot with both disks (original and cloned) attached because you will have identical UUID on two disks and conflict will ensue.

Is this your first time with Clonezilla?

If so, be very cautious and make sure that you have [COLOR="#0000FF"]personal data [/COLOR]backups.

---

### Post by pretty_whistle on 2020-11-05
Thanks for the help.  Now I know what to do, I'll have to do a fresh install onto the SSD, my backup cannot be used since it's too big.

---

